all: do.json do.zip

R_OPTS=--no-save --no-restore --no-init-file --no-site-file # --vanilla, but without --no-environ

Orig/Gatti_2014_pheno.csv:
	[ -d Orig ] || mkdir Orig
	curl https://phenomedoc.jax.org/QTL_Archive/gatti_2014/$(@F) > $@

Orig/Gatti_2014_geno.csv:
	[ -d Orig ] || mkdir Orig
	curl https://phenomedoc.jax.org/QTL_Archive/gatti_2014/$(@F) > $@

Orig/muga_code.Rdata:
	[ -d Orig ] || mkdir Orig
	curl ftp://ftp.jax.org/MUGA/$(@F) > $@

Orig/muga_geno.Rdata:
	[ -d Orig ] || mkdir Orig
	curl ftp://ftp.jax.org/MUGA/$(@F) > $@

Orig/muga_snps.Rdata:
	[ -d Orig ] || mkdir Orig
	curl ftp://ftp.jax.org/MUGA/$(@F) > $@

do.json: Code/convert_data.R Orig/Gatti_2014_geno.csv Orig/Gatti_2014_pheno.csv Orig/muga_code.Rdata Orig/muga_geno.Rdata Orig/muga_snps.Rdata
	cd Code;R $(R_OPTS) -e 'source("$(<F)", echo=TRUE)'

do.zip: do.json
	zip do.zip do.json do_*.csv
