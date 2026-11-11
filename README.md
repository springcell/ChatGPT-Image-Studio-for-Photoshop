# ChatGPT Image Studio for Photoshop

**English** | [简体中文](README.zh-CN.md)

[Download v0.3.7 preview](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/releases/tag/v0.3.7) · [Installation](#download-and-install-windows) · [Drawing Skills](#drawing-skills-preview) · [Feedback](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/issues)

**Local Edition v0.3.7 · Skill preview** · Windows · Adobe Photoshop 25.2+ · UXP

**AI image generation, region-guided editing, and reusable drawing Skills in Photoshop.**

ChatGPT Image Studio combines natural-language image generation with a compact Photoshop editing toolbar. Generate new artwork, guide edits with image-region comments, remove backgrounds or objects, and expand a composition to a new aspect ratio.

<p align="center">
  <img src="docs/images/06-edited-result.png" alt="AI-edited anime sci-fi artwork inside Photoshop" width="590">
</p>

<p align="center"><strong>Prompt · Comment · BG · Erase · Size</strong></p>

> [!NOTE]
> This is an **independent, community-made Photoshop integration**, not an official Adobe or OpenAI product. Model options, API availability, output behavior, and installation screens may vary by release. Screenshots illustrate the workflow; they do not prove every model/provider combination was tested.

## Drawing Skills preview

The v0.3.7 preview adds a way to reuse drawing instructions and reference assets:

- Import and manage a Skill from a ZIP, a `SKILL.md` file, or a folder.
- Select a Skill for image generation and choose whether to attach its resource images.
- No separate Runner or additional service is required for the Skill feature. Skill scripts and extension steps are not executed.

> [!WARNING]
> **Preview, not a validated production release.** According to the package notes, v0.3.7 has passed offline tests, but Photoshop-host acceptance and live image-API requests have **not** been verified. Keep a previous working version for rollback. The screenshots and detailed workflow below document v0.3.5; they are not proof that v0.3.7 has passed end-to-end testing.

**Start here:** [v0.3.7 release notes and plugin download](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/releases/tag/v0.3.7). The separate [v0.3.5-docs release](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/releases/tag/v0.3.5-docs) contains documentation only, **not the plugin installer**.

## Download and install (Windows)

**Requirements:** Windows, **Adobe Photoshop 25.2 or later**, [Adobe UXP Developer Tool (UDT)](https://developer.adobe.com/photoshop/uxp/2022/guides/devtool/), internet access for remote image generation, and an API credential for the provider you want to use.

1. Open the **[v0.3.7 preview release](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/releases/tag/v0.3.7)** and download **`chatgpt-image-studio-local-0.3.7-skills.zip`** from **Assets**. Do not choose the documentation-only ZIP or GitHub's automatically generated source archives.
2. **Extract all files** to the `Plug-ins` folder. Keep the whole extracted folder together; the Photoshop plugin loads files from `plugin/`.
3. Double-click **`Install.cmd`** in the extracted folder. This installs and starts the **desktop floating toolbar**; it does **not** automatically install the Photoshop panel.
4. Open **Adobe UXP Developer Tool (UDT)**. Choose **Add Plugin**, browse to **`plugin/manifest.json`** in the extracted folder, and then **Load** the plugin from UDT.
5. In Photoshop, open the **chatgpt image studio Local** panel from the **Plugins** menu (location can vary by Photoshop version).
6. Keep the extracted bundle in place while using the plugin. After updating the extracted files, run **`Install.cmd`** again and reload the manifest in UDT.

The release notes identify these setup files. Keep **all** extracted files, not only the files shown here:

```text
extracted-release-folder/
├── Install.cmd              # Installs desktop toolbar
├── SKILLS_README.md         # Skill usage, limitations, and rollback
└── plugin/
    └── manifest.json        # Load this file in UDT
```

> [!IMPORTANT]
> Run `Install.cmd` **and** load `plugin/manifest.json` via UDT. These are two different setup steps and both are required.

## First-time setup

The settings and screenshots in this section describe the v0.3.5 workflow. For v0.3.7 Skill usage, limitations, and rollback, read `SKILLS_README.md` in the downloaded package. Remote image generation still requires your chosen provider's API access; the Skill feature does not supply an API account or credits.

1. Open the Photoshop plugin panel and click the **settings icon** in the top-right corner.
2. Set **Language** (`English` or `Chinese`) and **Provider** (for example, OpenAI or a compatible gateway such as sub2api).
3. For the official OpenAI API, leave **API base URL** blank to use the default `https://api.openai.com/v1`, or enter it explicitly. For another provider, use the endpoint supplied by that provider.
4. Enter your **API Key**. The plugin uses **local UXP secureStorage** for API configuration; according to the package documentation, it does not send the API key to the desktop toolbar.
5. Choose an available **Image model**. Version 0.3.5 includes **Flare 2.5**, **Sunburst 2.5**, **Flare 2.6**, and **Sunburst 2.6** provider-facing options. Actual access depends on your provider.
6. Click **Save settings**, then **Test API**. The API test requests the **model list only**; it does **not** verify image-generation permission or performance.
7. Enable **Remember edits** if desired. Use **Show toolbar / Hide toolbar** to toggle the floating toolbar.

<p align="center">
  <img src="docs/images/02-settings.png" alt="Local API settings with language, provider, URL, key, model selection and Test API" width="420">
</p>

> [!NOTE]
> **Model compatibility in v0.3.5 (per bundled release notes):** Sunburst 2.6 passed a direct non-streaming generation check. Flare 2.6 is **unverified**; 2.6 streaming, editing, Photoshop-host integration, and sub2api compatibility **still require testing**. The names are provider-facing labels; they do not establish official public OpenAI model IDs.
>
> When changing your API provider or endpoint, re-enter your API key. Use HTTPS for public endpoints; HTTP on local/private LAN connections is unencrypted.

## Generate your first image

1. In **Describe your idea**, write a visual prompt. For example:

   > Generate a sci-fi anime-style female warrior standing before ruins.

2. Optionally enable **Prompt cleanup**, add **References** (up to 16 are shown in the example UI), or choose **Use PS selection** to supply your current Photoshop selection as a reference.
3. Set **Width** and **Height** (or choose an available preset). Choose **Quality** and **Background**: `Auto`, `Transparent`, or `Opaque`.
4. Click **Generate image**.
5. A **partial preview** may appear during generation. Allow the request to complete; the example workflow opens the **final result in a new Photoshop document**.

<p align="center">
  <img src="docs/images/01-generate-panel.png" alt="Photoshop plugin panel showing prompt entry, reference selection, 1024x1024 settings, a partial preview and Stop button" width="420">
</p>

**Example result**

<p align="center">
  <img src="docs/images/03-original-image.png" alt="Generated anime sci-fi warrior with a glowing sword in ruined futuristic architecture" width="500">
</p>

**Tip:** Use the aspect ratio you actually need. When the requested dimensions differ from the generated composition, the plugin may fit or crop the image to the canvas, as indicated in the request summary.

## Floating toolbar at a glance

After an image is open in Photoshop and the desktop toolbar is enabled, five editing actions are available:

<p align="center">
  <img src="docs/images/10-toolbar.png" alt="Floating toolbar with Prompt, Comment, BG, Erase and Size actions" width="675">
</p>

| Action | What it does |
|:--|:--|
| ![Prompt icon](docs/images/tool-prompt.png) | Describe a new edit in plain language and send it to the image model. |
| ![Comment icon](docs/images/tool-comment.png) | Place separate instructions on specific regions of the image. |
| ![BG icon](docs/images/tool-background.png) | Work with the background, including creating transparent-background output. |
| ![Erase icon](docs/images/tool-erase.png) | Select an unwanted area and have it removed/reconstructed. |
| ![Size icon](docs/images/tool-size.png) | Change the framing/aspect ratio and generate the additional composition. |

### 1. Prompt — describe a change

Select **Prompt** from the toolbar, type what you want to create or change, then click **Send**. Use clear instructions about the subject, environment, color, or desired edit.

<p align="center">
  <img src="docs/images/04-prompt-dialog.png" alt="Prompt dialog with an editable instruction and Send button" width="590">
</p>

### 2. Comment — direct edits by region

Select **Comment** to open **Region comments**. Mark individual regions on the picture, give each region its own instruction, and click **Send** to apply the edit request.

In this example, three instructions are attached to the artwork:

1. **Remove the weapon** — next to the hand and sword.
2. **Smile** — over the character's face.
3. **Mechanical bird** — in the sky.

<p align="center">
  <img src="docs/images/05-region-comments.png" alt="Three region comments over the image with instructions to remove the weapon, smile, and add a mechanical bird" width="820">
</p>

**Result:** The weapon is gone, the facial expression changes, and a mechanical bird appears above the ruins.

<p align="center">
  <img src="docs/images/06-edited-result.png" alt="Edited image with weapon removed and a mechanical bird added to the sky" width="590">
</p>

### 3. BG — work with the background

Choose **BG** for a background operation, such as producing a transparent-background image. This is especially useful for character art, game assets, stickers, and compositing.

<p align="center">
  <img src="docs/images/07-transparent-background.png" alt="Character and mechanical bird isolated on a transparent Photoshop checkerboard" width="610">
</p>

**Tip:** Zoom in around hair, fabric, and thin shapes to inspect edge quality before exporting the asset.

### 4. Erase — remove an unwanted object

Choose **Erase**, use Photoshop's **freehand lasso** to select the area to remove, and click **Send**. The plugin requests reconstruction of the selected region using its surroundings.

<p align="center">
  <img src="docs/images/08-erase-selection.png" alt="Lasso selection over unwanted background architecture and the Erase action prompt" width="640">
</p>

**Tip:** Select the complete unwanted object plus a small margin for more reliable reconstruction. Keep an original document or layer as a backup before major edits.

### 5. Size — expand or reframe the image

Choose **Size** and select the destination aspect ratio, then click **Generate**. The example menu provides:

| Portrait / square | Landscape |
|:--|:--|
| **1:1** Square | **4:3** Landscape |
| **3:4** Portrait | **16:9** Widescreen |
| **9:16** Story | |

This example expands the original portrait-oriented composition into a widescreen scene rather than stretching the character.

<p align="center">
  <img src="docs/images/09-resize-dialog.png" alt="Expanded sci-fi artwork with the Size toolbar action and Widescreen 16:9 selected" width="840">
</p>

## Tips for consistent results

- **Be specific.** Mention subject, style, materials, lighting, composition, and what must stay unchanged.
- **Localize edits.** Prefer a small lasso selection or a region comment when editing one detail.
- **Use references.** Attach reference images or **Use PS selection** when you need continuity with existing artwork.
- **Preserve your source.** Save your `.psd` and keep a backup before large edits or aspect-ratio expansion.
- **Check transparency.** Inspect fine hair, soft edges, and translucent materials against contrasting backgrounds.
- **Pick a suitable ratio early.** Large changes in aspect ratio may require generating new surroundings.

## Troubleshooting

If the floating toolbar fails to start, run **`Diagnose.cmd`** from the extracted release folder, then read its output. The desktop executable in this 0.3.5 package is carried over from the 0.3.3 desktop component.


<details>
<summary><strong>Photoshop doesn't show the plugin</strong></summary>

Confirm Adobe Photoshop is version **25.2+**, check that the entire ZIP was extracted, and verify that **UDT loaded `plugin/manifest.json`**. Restart Photoshop if necessary. `Install.cmd` installs the toolbar but does not load the panel.

</details>

<details>
<summary><strong>Test API fails</strong></summary>

Click **Save settings** before **Test API**. Check your provider, endpoint, API key, supported model, and network. **Test API only reads the model list**, so an image request may still fail even after a successful test. Never post raw API keys in diagnostics.

</details>

<details>
<summary><strong>The result is cropped or the framing is wrong</strong></summary>

Match the input composition to the desired output ratio, and review the request summary before generating. Use **Size** when you want additional scene content instead of a simple crop.

</details>

<details>
<summary><strong>A local edit changes too much</strong></summary>

Use a smaller selection or separate region comments. State exactly which elements should remain unchanged and try the edit again from your original document.

</details>

<details>
<summary><strong>Generation is slow or a preview appears to be stuck</strong></summary>

A partial preview is not the completed output. Check the elapsed-time and status messages; if the request fails, review network access, provider rate limits, selected model, and output settings. The **Stop** button cancels an active request.

</details>

## Uninstall

Run **`Uninstall.cmd`** from the extracted release folder to stop the Local desktop toolbar and remove its automatic-start entry. **The uninstaller retains configuration and files.** If you want to remove the Photoshop panel too, unload/remove it from UDT; delete the extracted bundle only after you no longer need it. To clear stored API credentials, click **Clear key** in the plugin settings **before** uninstalling.

## Release verification

File: `chatgpt-image-studio-local-0.3.7-skills.zip`

SHA-256 recorded on the v0.3.7 release asset:

```text
8d1d5910c956d43e60eea3a3cdd77dffa974bfd8aedb6917c9d7f10b5abd9a0a
```

Compare the downloaded file's SHA-256 with this value before installation. A matching checksum confirms file consistency, **not** a malware audit or end-to-end Photoshop/API validation.

## Try it and share feedback

[Download the preview](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/releases/tag/v0.3.7) and try it with a copy of your artwork. For a reproducible problem, [open an issue](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/issues) with your Windows and Photoshop versions, plugin version, provider/model label, steps, expected result, and actual result. **Do not include API keys or private artwork.**

For workflow ideas and examples you have permission to share, use [Discussions](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop/discussions). If the project is useful to you, a GitHub star helps others discover it.

## License and attribution

This repository uses the [Apache License 2.0](LICENSE). Adobe and Photoshop are trademarks of Adobe Inc.; OpenAI and ChatGPT are trademarks of OpenAI. This project is independently developed and is not endorsed by either company.

**Repository:** [springcell/ChatGPT-Image-Studio-for-Photoshop](https://github.com/springcell/ChatGPT-Image-Studio-for-Photoshop)  
**Read this guide in Chinese:** [简体中文 README](README.zh-CN.md)
