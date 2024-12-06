# Taji CV

This CV is built using LaTeX and inspired by the project: [Maths Template](https://www.overleaf.com/latex/templates/maths-volunteers/fgfrfcjgrxhj).

All the data used in the CV is fictional, as I didn’t want to expose my personal information. Therefore, I used dummy and AI-generated content. However, it reflects my cyber security journey. Feel free to fork this repository and modify the content for your own use.

## Features
- Clean and professional layout.
- Easily customizable for any profession.

Built with LaTeX.

# Automated Workflow: GitHub Actions

If you only need to update the content and don’t want the hassle of maintaining an offline setup, you can use GitHub Actions to compile the LaTeX code and publish your CV as a release artifact.

### Workflow Overview:
1. Triggering the Workflow:
	- The GitHub Actions workflow is triggered automatically on changes pushed to the master branch or manually via the “Run Workflow” button.
2.	Compilation and Publishing:
	- The workflow compiles the LaTeX code, uploads the generated PDF (cv.pdf) as a release artifact, and publishes it directly to [releases here](https://github.com/sht/taji-cv/releases).
3.	Benefits:
	- No need to set up a local LaTeX environment.
	- Ensures consistency and reliability by running on GitHub’s servers.
	- Easily share the CV PDF by downloading it from the release.

### Linking the Workflow

The GitHub Actions workflow is defined in [.github/workflows/latex-ci.yml](.github/workflows/latex-ci.yml). Here’s a brief explanation:

When changes are pushed to the master branch, the workflow:
1. Checks out the repository.
2. Compiles the LaTeX file using `Latexmk` on GitHub’s server.
3. Uploads the generated `cv.pdf` as a release artifact with a unique tag name.

With this setup, your `cv.pdf` is compiled and uploaded as a release artifact whenever changes are merged into the master branch. 

Choose the **offline setup** for development purposes, but rely on **GitHub Actions** for quick updates and hassle-free publishing of your CV PDF.

# Offline Setup: TinyTeX Installation

For development purposes, you can use lightweight `TinyTeX`: A lightweight, cross-platform, portable, and easy-to-maintain LaTeX distribution based on TeX Live. 

## Installation

To install `TinyTeX` on macOS, use the following command:

```bash
curl -sL "https://yihui.org/tinytex/install-bin-unix.sh" | sh
```

`tlmgr` is the package manager which is installed now with `TinyTeX`.

For installing the required packages, make sure all dependencies mentioned in [requirements.txt](./requirements.txt) are installed. On macOS, you can install all the necessary packages with the following command:

```
tlmgr install $(tr '\n' ' ' < requirements.txt)
```
Sometimes, you may need to re-run this command multiple times to ensure all packages are installed.

## Compilation

After installation, you can compile the TeX document with the pdflatex command. For example:

```bash
pdflatex cv.tex
```

To simplify the compilation process, I aliased `pdflatex` to `px` in `.zshrc` for convenience.

Now, it’s easy to run: `px cv.tex` 🍻

## Common Errors and Solutions

During compilation, you might encounter errors if not all the packages from [requirements.txt](./requirements.txt) are installed.

For example:

```shell
! LaTeX Error: File `titlesec.sty' not found.

Type X to quit or <RETURN> to proceed, or enter new name. (Default extension: sty)
```
To resolve this, search for the file with the following command:

```bash
tlmgr search --global --file "/titlesec.sty"
```

This will return the package name:

```bash
tlmgr: package repository https://mirror.physik.tu-berlin.de/pub/CTAN/systems/texlive/tlnet (verified)
titlesec:
	texmf-dist/tex/latex/titlesec/titlesec.sty
```

Install the required package with:

```bash
tlmgr install titlesec
```

Initially, I encountered many such errors and resolved them by installing the appropriate packages. All the necessary packages have been exported in [requirements.txt](./requirements.txt), so you likely won’t run into these issues, but it’s still good to learn how to troubleshoot them.

Even after installing all the packages, I encountered this error:

```bash
! LaTeX Error: This NFSS system isn't set up properly
```

To fix it, install the `cbfonts-fd` package:

```bash
tlmgr install cbfonts-fd
```

I found this solution [here](https://github.com/ulyngs/oxforddown/issues/4#issuecomment-645474992) because the error message did not clearly indicate which package was needed.

## Uninstallation

To remove the installation in the future, use the following commands:

```bash
tlmgr path remove
rm -r ~/Library/TinyTeX
```
