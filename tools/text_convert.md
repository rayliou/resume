
```
- pandoc --pdf-engine=xelatex   CV_C++.md -o  /mnt/c/Jobs-工作/CV_C++.md_2.pdf
```
为了在 Ubuntu 系统上使用 Pandoc 和 XeLaTeX 生成 PDF，并确保这些 PDF 在 Windows 系统上查看时具有良好的视觉效果，请遵循以下指南：

### 安装 Pandoc 和 XeLaTeX

1. **更新软件包列表**：
   打开终端并执行以下命令，以确保 Ubuntu 的软件包列表是最新的。
   ```bash
   sudo apt-get update
   ```

2. **安装 Pandoc**：
   使用以下命令安装 Pandoc，这是一个强大的文档转换工具。
   ```bash
   sudo apt-get install pandoc
   ```

3. **安装 XeLaTeX**：
   XeLaTeX 是一个 LaTeX 引擎，支持现代字体系统。通过安装 `texlive-xetex` 包来获取 XeLaTeX。
   ```bash
   sudo apt-get install texlive-xetex
   ```

### 设置字体

为了确保 PDF 在 Windows 上具有良好的视觉效果，请选择广泛支持的字体，如“Times New Roman”、“Arial”和“Courier New”。首先，安装微软字体：

1. **安装微软字体**：
   在 Ubuntu 上，通过以下命令安装微软的 TrueType 核心字体。
   ```bash
   sudo apt-get install ttf-mscorefonts-installer
   ```
   安装完成后，执行 `fc-cache -f -v` 更新字体缓存。

### 使用 Pandoc 和 XeLaTeX 生成 PDF

1. **准备 Markdown 文件**：
   在 Markdown 文件的头部添加 YAML 块，以指定字体。替换 `input.md` 为你的文件名。
   ```yaml
   ---
   header-includes:
      - \usepackage{fontspec}
      - \setmainfont{Times New Roman}
      - \setsansfont{Arial}
      - \setmonofont{Courier New}
   ---
   ```

2. **生成 PDF**：
   使用 Pandoc 和 XeLaTeX 将 Markdown 文件转换为 PDF，确保字体设置正确应用。
   ```bash
   pandoc input.md -o output.pdf --pdf-engine=xelatex
   ```

通过遵循上述步骤，你可以在 Ubuntu 上生成在 Windows 系统上查看时外观优雅的 PDF 文档。这样的设置确保了文档在不同平台之间具有良好的兼容性和一致的视觉效果。
