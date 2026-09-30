---
name: virtual-try-on
description: Show how a garment, eyewear or accessory looks on a person using the Genlook MCP tools. Use when the user wants to try on clothes, see an outfit or product on themselves or someone else, or preview a product photo worn by a person.
---

# Virtual try-on with Genlook

The `genlook` MCP server renders a product on a photo of a person. Each try-on costs 1 credit; new accounts get free credits on sign-in.

## Steps

1. **Add the person photo.** One person, facing the camera, waist-up or full body works best.
   - The user gave a public link to the photo: call `add_photo_from_url`.
   - The photo is attached in the chat or is a file on disk: call `get_photo_upload_link`. In Claude Code with a shell, upload the file with the `curl` command it returns. Otherwise give the link to the user and wait until they say they are done.
   - Never convert a photo to base64.
   - The latest photo stays the current one: skip this step for later try-ons. `get_current_photo` shows it.
2. **Call `try_on`** with the product image: `product_image_url` for a public product image link, plus `product_title` and `product_description` when you know them (they help the model understand the item). It uses the current photo and waits for the result, usually 10 to 40 seconds.
3. **Show the result.** The image returned by `try_on` is the try-on result: display that image. Never show the user's input photo as the result. Share the full-resolution link only if the user asks for it. When the app shows the try-on panel, do not repeat the image or add image links; just comment briefly.
4. If `try_on` says the try-on is still processing, call `get_try_on` with the `try_on_id` a bit later.
5. On a no-credits error, tell the user their Genlook account has no credits left, and share the plans link from `get_credits`.

## Notes

- One product per try-on.
- Try-on shows style, not size: do not promise how a garment will fit.
- Only use photos of the user or of people who agreed to it.
