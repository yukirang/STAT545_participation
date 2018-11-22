all: report.html

clean:
	rm -f words.txt histogram.tsv histogram.png report.Rmd

words.txt:
	Rscript -e 'download.file("https://svnweb.freebsd.org/base/head/share/dict/web2?view=co", destfile = "words.txt", quiet = TRUE)'
	
histogram.tsv: histogram.R words.txt
# Rscript histogram.R
	Rscript $<
	
histogram.png: histogram.tsv
# Rscript -e 'library(ggplot2); qplot(Length, Freq, data=read.delim("histogram.tsv")); ggsave("histogram.png")'
# Rscript -e 'ggplot2::qplot(Length, Freq, data=read.delim("$<")); ggplot2::ggsave("$@")'
	Rscript -e 'library(ggplot2); qplot(Length, Freq, data=read.delim("$<")); ggsave("$@")'
	rm -f Rplots.pdf


	
	