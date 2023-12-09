# Phase 2. Work environment setup

In this course you will make use of different software packages and tools. In this phase we will install and configure the necessary applications for an efficient work environment.

## Software Installation 

This is what you need:

- A Git client ([Git CLI](https://git-scm.com), [Gitkraken](https://git-scm.com), ...)
- A LaTeX-distribution:
    - Windows: [MikTeX](https://miktex.org) of [TeX live](https://www.tug.org/texlive/) (recommended)
    - MacOS X: [MacTeX](https://www.tug.org/mactex/)
    - Linux: [TeX live](https://www.tug.org/texlive/))
- A LaTeX IDE or editor with LaTeX support:
    - [Texstudio](https://www.texstudio.org) is a complete IDE, specifically for LaTeX (recommended)
    - [Visual Studio Code](https://code.visualstudio.com) has good support, but requires some fiddling [configuring](https://dev.to/ucscmozilla/how-to-create-and-compile-latex-documents-on-visual-studio-code-3jbk)
- [JabRef](https://www.jabref.org), a bibliografic database specifically for LaTeX
- An editor with Markdown support is also convenient
    - [Visual Studio Code](https://code.visualstudio.com) has excellent support (i.e. HTML preview with `Ctrl+Shift+V`)
    - [Typora](https://typora.io)

### Windows

We suggest to use [Chocolatey Package Manager](https://chocolatey.org/install) for the management of installed applications.

Open a Powershell or CMD terminal as Administrator and select from the commands listed below for the specific packages you'd like to install. Please notice that text behind the (`#`) symbol is not executed, hence does not need to be copied and is interpreted as a comment!

```powershell
choco install -y git        # CLI client
choco install -y gitkraken  # Graphical Git client (optional)
choco install -y miktex     # LaTeX distribution
choco install -y texlive    # Alternatieve LaTeX distro (choose either one, but only 1!)
choco install -y texstudio  # Complete LaTeX IDE
choco install -y vscode     # Visual Studio Code (optional)
choco install -y JabRef     # Bibliographic database
choco install -y typora     # Markdown editor (optional)
```

### MacOS X

We suggest to use the [Homebrew package manager](https://brew.sh/) for the management of installed applications. *Please notice: this procedure has not been tested recently, any feedback will be appreciated!*

Open a Terminal and select from the commands below the specific packages that you would like to install. Please notice that text behind the (`#`) symbol is not executed, hence does not need to be copied and is interpreted as comment!

```bash
brew install git               # CLI client
brew install --cask gitkraken  # Graphical Git client (optional)
brew install --cask mactex     # LaTeX distribution
brew install --cask texstudio  # Complete LaTeX IDE
brew install --cask visual-studio-code # VS Code (optional)
brew install --cask jabref     # Bibliographic database
brew install --cask typora     # Markdown editor (optional)
```

### Linux (Debian/Ubuntu)

Linux users know that there are differences in software installation procedures, depending on the distribution. A few instructions for distributions from the Debian-family (Ubuntu, Mint, enz.). For other distributions the command and package names can differ, but Linux users are generally aware of this.

```bash
sudo apt install git        # CLI client
sudo apt install texlive    # LaTeX distribution
sudo apt install texstudio  # Complete LaTeX IDE
sudo apt install jabref     # Bibliographic database

wget https://release.gitkraken.com/linux/gitkraken-amd64.deb
sudo dpkg -i gitkraken-amd64.deb  # Graphical Git client (optional)

# Download the .deb package first from https://code.visualstudio.com/Download
sudo dpkg -i ./code_*.deb   # VS Code
```

De **TeX live** distribution is very extensive and was divided into different packages. `texlive` is the basic installation, `texlive-full` the complete distribution (including parts you might never need). The choice is yours: either you install TeX live completely, either the basic installation complemented with the extra features you need, e.g. `texlive-science`, `texlive-xetex`, etc. For a detailed overview of available features you can explore the `apt search texlive`. You will have to find out for yourself what you really need and what you have to install additionally.

## Configuration Git, Github

Normally, you should have already made a Github-account and personal Github repository via the Github Classroom link that you can find on the Chamilo platform.

### Basic configuration

Before you will use Git on your laptop it is important to configure some **basic settings**. If you won't, your commits will not always be pushed correctly to github in your name. Especially for group assignments, this is a problem as it is impossible to distinguish between your contributions and your fellow students'!

- Connect your **HoGent email address** to you Github account (you can register multiple addresses). This way, you can claim a [Github student developer pack](https://education.github.com/pack), allowing free access to some paying products and services.
- [Generate an SSH key pair](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) if you haven't already and [register it on Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
- Set up your name and (HOGENT-) email. Using the CLI:

    ```console
    git config --global user.name "Pieter Stevens"
    git config --global user.email pieter.stevens.u12345@student.hogent.be
    git config --global github.user PieterStevens
    ```

- Adapt [some basic settings](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration) :

    ```bash
    git config --global push.default simple
    git config --global pull.rebase true
    git config --global rebase.autoStash true
    git config --global init.defaultBranch main
    ```

    Please go through the [documentation](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration) to find out what these commands do.

- Clone your Github-repo onto your laptop.

### Recommendations

We assume that you are able to work with Git/Github! Some recommendations:

- **Avoid** using the **Github webinterface** for adding/adapting file content. Clone your repository locally onto your laptop and use the command-line or a decent GUI. 
- **Commit and push** as often as possible!
- Create [**atomic commits**](https://dev.to/cbillowes/why-i-create-atomic-commits-in-git-kfi). Your github-repository is a backup that helps you from losing your work in progress. 
- Provide a clear description for your commits in the [**commit messsage**](https://cbea.ms/git-commit/).
- The standard for formatted text on Github is [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax). Please take your time to learn how to write a **Markdown document** and explore its layout (in an editor or on Github).

## LaTeX

LaTeX has been around for some decades. Before, it was only possible to write a LaTeX document using ASCII characters while today it is fully UTF-8 compatible. Most LaTeX related tools still have those original settings. Therefore some configuration adjustments are needed!

### TeXStudio configuration

Check these settings using menu item *Options > Configure TeXstudio*

- Build:
    - Default Compiler: **XeLaTeX** (UTF-8 compatible, possibility to use TTF (true type font) etc.) instead of PDFLaTeX (only ASCII, PostScript fonts, etc.)
    - Default Bibliography tool: **`biber`** (UTF-8 compatible, APA referencing support, ...) instead of `bibtex` (only ASCII, no APA referencing, ...)
- Commands:
    - XeLaTeX: `xelatex -synctex=1 -interaction=nonstopmode -shell-escape %.tex` (add the option `-shell-escape`)
- Editor:
    - Indentation mode: *Indent and Unindent Automatically*
    - Replace Indentation Tab by Spaces: *Check*
    - Replace Tab in Text by spaces: *Check*
    - Replace Double Quotes: *English Quotes: ``''*

To test proper functioning of TeXStudio, you can use the template for the paper ( `paper/SurnameFirstnameYearRM.tex`) gebruiken. First change the file name to your own name (surname first) and the year (e.g. `DeSmetJan2022RM.tex`).

Choose *Tools > Build & View* (or function key `F5`) to compile into a PDF file. **Plese notice!** If the resulting PDF file does not contain a bibliography, you will have to compile it separately. You can do this using the menu *Tools > Bibliography* or function key `F8`. Afterwards *Build & View* again.

Many LaTeX functionalities are available in separate packages that are not necessarily installed by default. The first time you compile a file, there is a great chance that you will need to download extra packages. MiKTeX on Windows will provide you with a pop up window to ask for your permission to install them. If so, just confirm. The first compilation might take some minutes without any feedback on what is going on, just remain patient. On Linux this might not work automatically, and you will need to find out what extra `texlive` packages are needed to reach the desired functionality.

In case of any compilation errors, you can find the tab page *Log* to get an overview of the error messages. When asking your lecturer for help, it is important to provide the **exact error message**. The easiest way to do this, is to select and copy the whole tab page *Log file*. 

### Visual Studio Code

VS Code is a powerful text editor with good support for many programming and scripting languages. Moreover, structured text formats like HTML, Markdown, etc. Also for LaTeX there are decent plugins. When you are familiar with VS Code already, you might want to use it for editing LaTeX files as well. The disadvantage is the configuration of VS Code. Being rather complex, we will not describe an extensive road map here. 

In any case install James Yu's [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop). Adjust the configuration so the `xelatex` compiler is used instead of the `pdflatex` one. Read [the documentation](https://github.com/James-Yu/LaTeX-Workshop/wiki) for more information and get inspired by [this VS Code configuration file](https://github.com/bertvv/dotfiles/blob/master/.config/Code/User/settings.json) to configure LaTeX Workshop.

### JabRef

[JabRef](http://www.jabref.org/) is a GUI for editing BibTeX files, a kind of database with sources from the academic or professional literature for a LaTeX document. The interface and settings vary between versions, so it is possible that these instructions are not up to date anymore depending on the version.

Inside the LaTeX world, there is a separate subsystem to correctly set up a reference list or bibliography. The "old" system is called BibTeX and is often the default option in LaTeX editors. The template for the paper and also the one used for your bachelor thesis is based on a modern replacement, BibLaTeX/biber. Adapt Jabref to use the latter by default.

- Choose *Options > Preferences > General* in the menu and choose the option "Default bibliography mode" at the bottom for "biblatex".
- Choose in the *Preferences* window the category *File* and supply a directory for storing the PDF files of the found sources for the option *Main file directory*. It is strongly advised to download and store the found articles and keep them in the specified directory. Even better is to use the BibTeX key as name for the stored file (typically the surname of the first author + year, e.g. Knuth1998.pdf). This is convenient to open the file from within Jabref.

## Write the introduction

If you chose a final topic in the previous phase, you can write the introduction of the paper in the LaTeX document in the `paper/` directory (which you should have renamed to match your own name(s)).

## Checklist

- [ ] The necessary software is installed.
- [ ] The basic Git settings are adapted where required. On committing, it is obvious who the author is. 
- [ ] TeXstudio or VS Code are configured for use.
- [ ] The template compiles without errors, in the generated PDF the (example) bibliography is present.
- [ ] You've written out the introduction of your research subject
