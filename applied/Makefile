# Define the output directory
OUTPUT_DIR=/mnt/c/Jobs-工作

# Find all Markdown files in the current directory
MD_FILES=$(wildcard *.md)

# Replace the .md extension with .pdf and prepend the output directory to the filenames
PDF_FILES=$(patsubst %.md,$(OUTPUT_DIR)/%.pdf,$(MD_FILES))

# Default target
all: $(PDF_FILES)

# Rule to convert each Markdown file to PDF, using pattern substitution for filenames
$(OUTPUT_DIR)/%.pdf: %.md
	pandoc --pdf-engine=xelatex $< -o $@

# Clean target to remove all generated PDFs in the output directory
clean:
	rm -vf $(PDF_FILES)
