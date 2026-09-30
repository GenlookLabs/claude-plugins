# Genlook Virtual Try-On

See any clothing, eyewear or accessory on a photo of a person, in about 10 seconds, without leaving Claude.

This plugin connects Claude to the Genlook MCP server (`https://mcp.genlook.app`) and adds a skill that walks Claude through a try-on: reuse or upload a person photo, send the product image with its title and description, and return the generated result.

## What it does and sends

- **Tools:** `upload_photo`, `get_uploaded_photo`, `generate_try_on`, `get_generation`, `get_account`, served by `https://mcp.genlook.app`. Nothing runs on your machine.
- **Data sent:** the person photo and product image you choose, plus the product title and description, go to Genlook to generate the try-on. Photos and results are deleted automatically after the retention window (7 days by default).
- **Account:** you sign in with a Genlook account through OAuth the first time Claude uses the tools. New accounts get 10 free credits; each try-on costs 1 credit. Top up at https://platform.genlook.app/topup.

## Use it

Ask Claude something like "try this jacket on my photo" with a product link and a photo. Only use photos of yourself or of people who agreed to it. Try-on shows style, not size.

Docs: https://genlook.app/docs/tryon-api/mcp · Privacy: https://genlook.app/privacy · Terms: https://genlook.app/terms · Support: hello@genlook.app
