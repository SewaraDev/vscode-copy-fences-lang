# Copy Fences (+Language)

> Fork of [mefengl/vscode-copy-folder-content](https://github.com/mefengl/vscode-copy-folder-content) that copies with **triple backticks** and a **language tag** inferred from the file extension (e.g., `.dart` → \`\`\`dart).

---

## ✨ Features

* Copy contents of **folders** and/or **selected files** to the clipboard as Markdown code blocks:

  * Uses **\`\`\`** (triple backticks) instead of six.
  * Adds a **language** after the opening fence, inferred from file extension (e.g., `.ts` → `typescript`, `.dart` → `dart`).
* Optional: **strip comments** before copying.
* **Recursive** copy and **filter by extensions**.
* Dedupes files and detects encoding (`jschardet` + `iconv-lite`).

> Each file is preceded by a separator line:
> `------ <relative-path> ------`

---

## 📦 Installation

### VS Code Marketplace

*After you publish*

* Command Palette → **Extensions** → search for **Copy Fences (+Language)** → **Install**
* Or via CLI:

```bash
code --install-extension SewaraDev.copy-fences-lang
```

### Open VSX (VSCodium/OSS)

*After you publish*

* Install from [open-vsx.org](https://open-vsx.org/extension/SewaraDev/copy-fences-lang)

### Local VSIX (no publishing required)

```bash
npm i
npx @vscode/vsce package
code --install-extension ./copy-fences-lang-<version>.vsix
```

---

## 🧪 Development

1. Clone and open:

```bash
git clone https://github.com/SewaraDev/vscode-copy-fences-lang
cd vscode-copy-fences-lang
npm i
```

2. Press **F5** to launch an *Extension Development Host* and test the context-menu commands.

> Tip: for faster activation, you can add explicit `activationEvents` in `package.json` (e.g., `onCommand:extension.copyFolderContent`).

---

## 🚀 Usage

Right‑click a **folder** or **file(s)** in the Explorer and choose a command:

| UI Title                                                | Command ID                                     | Context                                  |
| ------------------------------------------------------- | ---------------------------------------------- | ---------------------------------------- |
| Copy Folder Content (Markdown Fences + Lang)            | `extension.copyFolderContent`                  | Folder (non‑recursive)                   |
| Copy Folder Content Without Comments (Fences + Lang)    | `extension.copyFolderContentWithoutComments`   | Folder (non‑recursive, strips comments)  |
| Recursively Copy Folder Content (Fences + Lang)         | `extension.copyFolderContentRecursively`       | Folder (recursive)                       |
| Recursively Copy Folder Content by Type (Fences + Lang) | `extension.copyFolderContentRecursivelyByType` | Folder (recursive, filter by extensions) |
| Start New Collection with File                          | `extension.newCollectionAndAdd`                | File                                     |
| Add File to Collection                                  | `extension.addToCollection`                    | File                                     |
| Add File to Collection and Copy (Fences + Lang)         | `extension.addToCollectionAndCopy`             | File (copies immediately)                |
| Copy Collection and Clear (Fences + Lang)               | `extension.copyCollectionAndClear`             | File (over active collection)            |
| Copy Selected Files and Folders (Fences + Lang)         | `extension.copySelectedFilesAndFolders`        | Multi‑selection (files/folders)          |
| Copy Last Selection (Fences + Lang)                     | `extension.copyLastSelection`                  | Uses stored last selection               |

---

## 🧾 Output example

````
------ lib/main.dart ------
```dart
void main() {
  print('Hello, fences!');
}
```

------ src/app.ts ------
```typescript
export const hello = () => 'world';
```
````

> Files **without an extension** get a plain fence (no language tag).

---

## ⚙️ Configuration

No settings required. If you want options (e.g., custom header/separator template, force a language), open an issue/PR.

---

## 📐 Technical details

* **Language by extension:** simple mapping (e.g., `.dart` → `dart`, `.ts` → `typescript`, `.yml` → `yaml`). Unknown types fall back to the raw extension string.
* **Encoding detection:** attempts with `jschardet`; if not `utf-8`/`ascii` and confidence > 0.5, decodes via `iconv-lite`.
* **Strip comments:** applies `strip-comments` and collapses double blank lines.
* **Limits & safety:**

  * Selections with > **1000** files prompt for confirmation.
  * Selections with > **5000** files are **not** stored as "Last Selection" to avoid huge state.

---

## 🧭 Roadmap

* Special‑case well‑known files without extension (e.g., `Dockerfile`, `Makefile`, `.gitignore`).
* Configurable output template (header, separators, etc.).
* Optional keybindings.

---

## 🤝 Contributing

1. Fork and branch: `feat/<something>`
2. `npm i` → `npm run watch` for incremental builds
3. **F5** to test in the dev host
4. Use Conventional Commits (e.g., `feat(copy): triple backticks + language tag`)
5. Open a PR with description and examples

---

## 📝 License

MIT © SewaraDev.

Includes and credits the original work: [mefengl/vscode-copy-folder-content](https://github.com/mefengl/vscode-copy-folder-content).
