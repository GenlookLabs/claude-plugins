---
name: virtual-try-on
description: Show how a garment, eyewear or accessory looks on a person using the Genlook MCP tools. Use when the user wants to try on clothes, see an outfit or product on themselves or someone else, or preview a product photo worn by a person.
---

# Virtual try-on with Genlook

The `genlook` MCP server renders a product on a photo of a person. Each try-on costs 1 credit; new accounts get free credits on sign-in.

## Steps

1. **Get the person photo.**
   - If the user already uploaded one recently, call `get_uploaded_photo` and reuse its `imageId`.
   - Otherwise call `upload_photo` with a public `image_url` (or `image_base64` for a local file). One person, facing the camera, waist-up or full body works best.
2. **Get the product image.** A public URL of the product photo, flat-lay or worn by a model. Add the product title and description when you have them: they help the model understand the item.
3. **Call `generate_try_on`** with `garments: [{ image_url, title?, description? }]` and `person_image_id` (or `person_image_url`). It waits for the result and returns the image.
4. If it returns a `generationId` that is still processing, call `get_generation` a bit later.
5. On an insufficient-credits error, call `get_account` and point the user to the top-up link it returns.

## Notes

- One product per try-on.
- Try-on shows style, not size: do not promise how a garment will fit.
- Only use photos of the user or of people who agreed to it.
