DATE=$(shell date +'%Y%m%d')
OUTPUT_DIR=/mnt/c/Jobs-工作
MD_FILES=$(wildcard CV_*.md)

# Function to find the most recent PDF for each Markdown file
define find_recent_pdf
$(shell ls -t $(OUTPUT_DIR)/$(basename $(1))*.pdf 2>/dev/null | head -n 1)
endef


# Default target
all: $(addsuffix .pdf,$(basename $(MD_FILES)))
# Rule to build or rebuild the PDF only if necessary
%.pdf: %.md
	@recent_pdf=$(call find_recent_pdf,$<); \
	if [ -z "$$recent_pdf" ] || [ $< -nt $$recent_pdf ]; then \
		ls  -l $< $$recent_pdf ;\
		new_pdf=$(OUTPUT_DIR)/$$(basename $< .md)-$(shell date +'%Y%m%d').pdf; \
		echo "Building $$new_pdf from $<"; \
		pandoc --pdf-engine=xelatex $< -o $$new_pdf; \
	# else \
		# echo "Skipping $$recent_pdf, up to date."; \
	fi

# Clean target to remove all generated PDFs in the output directory
clean:
	rm -vf $(OUTPUT_DIR)/CV_*.pdf
