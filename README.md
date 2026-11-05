ChatGPT Image Studio for Photoshop
AI image generation and editing, directly inside Adobe Photoshop.

ChatGPT Image Studio brings a prompt-based image workflow into Photoshop. Generate new artwork, use reference images, edit selected regions, replace backgrounds, remove unwanted objects, and adjust canvas proportions without leaving your document.
[!NOTE]
This is an independent Photoshop plugin. It is not an official Adobe or OpenAI product. Available models and features depend on your connected service and plugin version.

Features
- Text-to-image generation — Create images from natural-language prompts.
- Selection-based editing — Target a Photoshop selection instead of regenerating the whole image.
- Reference images — Add images or import the active Photoshop selection as visual guidance.
- Prompt optimization — Optionally refine a prompt locally before sending it.
- Model selection — Choose between the available GPT Image 2.5 Flare and Sunburst options.
- Output controls — Set image width, height, quality, and background transparency.
- Contextual editing toolbar — Quickly access instructions, comments, background editing, erasing, and resizing.
- Photoshop-friendly workflow — Continue working with the generated result as a layer in your document.
Installation (Windows)
1. Download the latest plugin ZIP package from this repository's Releases page.
2. Extract the ZIP to a local folder.
3. Locate Install.cmd in the extracted folder and double-click it.
4. Follow the installer prompts until installation completes.
5. Restart Photoshop if it was already open.
6. In Photoshop, open Window → Extensions (or Plugins) → chatgpt image studio. The menu location may vary by Photoshop version.
A typical extracted package includes:
chatgpt-image-studio/
├── assets/
├── plugin/
├── Install.cmd
├── Install.ps1
└── README.txt
Only run installation scripts from a release you trust. If your system blocks the installer, inspect the included scripts and documentation before allowing them to run.

First-time setup
1. Open the chatgpt image studio panel in Photoshop.
2. Open the plugin's local connection/settings area.
3. Select an available image model.
4. Click Test Local Connection and Test API Connection to verify the setup.
5. Return to the main panel when both checks succeed.
The plugin UI indicates that API credentials are handled through its local service and held in plugin memory during use. Review the release's configuration and security documentation before entering credentials.
Generate an image
1. Enter your prompt in Describe your idea.
2. Optionally enable Optimize Prompt or add Reference Images.
3. Choose the resolution (preset or custom width × height).
4. Choose quality and a background mode: Auto, Transparent, or Opaque.
5. Click Generate Image.
The result can be added to the current Photoshop document as a new layer, so you can continue refining it with standard Photoshop tools.
Choose a model
The model selector in the plugin offers these options in the shown version:
Model	Suggested use
GPT Image 2.5 Flare	General-purpose generation and everyday image editing.
GPT Image 2.5 Sunburst	Images where a stronger lighting or atmosphere-oriented look is desired.


These descriptions reflect the plugin's UI guidance, not official benchmark claims. Model availability and behavior are determined by the connected service.
Contextual toolbar
When the contextual toolbar is enabled, Photoshop selections can be used to guide a more focused edit.
Tool	What it does
Instruction	Describe a change to generate, replace, or enhance content in a selected area.
Comment	Attach a text instruction to an area or element of the image. Use multiple comments to describe separate changes.
Background	Generate, replace, or extend background content.
Erase	Remove unwanted content from a selected or brushed region and fill it in.
Size	Change the output aspect ratio, including 1:1, 4:3, 3:4, 9:16, and 16:9.


Example: Add an object with Comments
1. Open an image in Photoshop.
2. Mark the area you want to change using a selection or the plugin's region annotation interface.
3. Choose Comment from the toolbar.
4. Enter an instruction such as "Add a small robotic dog here."
5. Send the instruction and review the generated result.
For more precise edits, select only the affected region and describe the desired change clearly.
Tips for better results
- Be specific about the subject, style, materials, lighting, and composition.
- Use a tight selection for local changes to avoid modifying unrelated content.
- Add reference images when appearance or composition needs to stay consistent.
- Use Transparent background for standalone assets and cutouts.
- Choose an output resolution appropriate for the final destination.
- Keep an original Photoshop layer or document backup before major edits.
Troubleshooting
The plugin panel does not appear.
Run Install.cmd again, restart Photoshop, and check the Window menu for the plugin. Verify that your Photoshop version supports the packaged extension type.

The local connection test fails.
Check whether the included local service has started and whether security software is blocking its connection. Use the package's diagnostic scripts if provided.

The API connection test fails.
Confirm that the connected service is configured correctly and that the selected model is available to your account or API provider.

Generation fails or takes too long.
Try a simpler prompt, a lower resolution, or a different available model. Check the error message and connection status.

A local edit changes too much.
Make a smaller selection and specify exactly what should stay unchanged.
Requirements and notes
- Adobe Photoshop on Windows with support for the packaged plugin/extension format.
- Access to the plugin's supported local service and an appropriately configured image API.
- An internet connection for remote image-generation requests.
- API access may be subject to provider fees, rate limits, and content policies.
Exact Photoshop versions, API setup steps, and supported image sizes should be checked against the specific release package.
Uninstall
Run Uninstall.cmd from the downloaded package (if included), then restart Photoshop.
Disclaimer
Adobe and Photoshop are trademarks of Adobe Inc. OpenAI and ChatGPT are trademarks of OpenAI. This repository is an independent integration and is not affiliated with or endorsed by either company.
