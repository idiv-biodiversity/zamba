# Minimal makefile for Sphinx documentation
#
S3_BUCKET=drivendata-zamba-docs

# You can set these variables from the command line.
SPHINXOPTS    = -W -vvv
SPHINXBUILD   = sphinx-build
SPHINXPROJ    = zamba
SOURCEDIR     = .
BUILDDIR      = _build

# Put it first so that "make" without argument is like "make help".
help:
	@$(SPHINXBUILD) -M help "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)

.PHONY: help Makefile

s3_upload: html
	aws s3 sync $(BUILDDIR)/html/ s3://$(S3_BUCKET) --acl public-read --delete

# Catch-all target: route all unknown targets to Sphinx using the new
# "make mode" option.  $(O) is meant as a shortcut for $(SPHINXOPTS).
%: Makefile
	@$(SPHINXBUILD) -M $@ "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O)
