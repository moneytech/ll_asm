CC = gcc
LFLAGS =
CFLAGS = -Wall -O3

all:	ll_document.pdf ll_total_new.eps new_graph out.eps out.png

out.png:		out.eps
			convert -density 600 -antialias -sample 400 out.eps out.png

out.eps:		out.jgr
			jgraph < out.jgr > out.eps
			
out.jgr:		new_graph
			./new_graph > out.jgr
			

new_graph:		new_graph.o
			$(CC) $(LFLAGS) -o new_graph new_graph.o
			
new_graph.o:		new_graph.c
			$(CC) $(CFLAGS) -c new_graph.c


ll_document.pdf:       ll_document.dvi
		       dvipdf ll_document.dvi

ll_document.dvi:       ll_document.tex \
		       architecture_table.tex \
		       correlations_table.tex \
		       ll_findstring_size.eps  ll_lzss_size.eps  \
		       ll_strcat_size.eps ll_total_size.eps \
		       ll_num_ascii.eps \
		       cache_graph.eps \
		       time_graph.eps \
		       libc_sizes.eps
		       latex ll_document.tex
		       
ll_total_new.eps:	      ll_total_new.jgr
		      jgraph < ll_total_new.jgr > ll_total_new.eps	
	
libc_sizes.eps:	      libc_sizes.jgr
		      jgraph < libc_sizes.jgr > libc_sizes.eps

cache_graph.eps:	   cache_graph.jgr
			   jgraph < cache_graph.jgr > cache_graph.eps

cpi_graph.eps:	   cpi_graph.jgr
			   jgraph < cpi_graph.jgr > cpi_graph.eps
			   
sizes_normal.eps:	   sizes_normal.jgr
			   jgraph < sizes_normal.jgr > sizes_normal.eps
			   
time_graph.eps:	   time_graph.jgr
			   jgraph < time_graph.jgr > time_graph.eps
			   
tlb_graph.eps:	   tlb_graph.jgr
			   jgraph < tlb_graph.jgr > tlb_graph.eps

uop_graph.eps:	   uop_graph.jgr
			   jgraph < uop_graph.jgr > uop_graph.eps
			   
			   


ll_total_size.eps:	   ll_total_size.jgr
			   jgraph < ll_total_size.jgr > ll_total_size.eps
			   
ll_lzss_size.eps:	   ll_lzss_size.jgr
			   jgraph < ll_lzss_size.jgr > ll_lzss_size.eps

ll_num_ascii.eps:	   ll_num_ascii.jgr
			   jgraph < ll_num_ascii.jgr > ll_num_ascii.eps

ll_strcat_size.eps:	   ll_strcat_size.jgr
			   jgraph < ll_strcat_size.jgr > ll_strcat_size.eps
			 
ll_findstring_size.eps:	   ll_findstring_size.jgr
			   jgraph < ll_findstring_size.jgr > ll_findstring_size.eps
			   

clean:	
	rm -f ll_total_size.eps ll_lzss_size.eps ll_strcat_size.eps \
	cache_graph.eps cpi_graph.eps ll_num_ascii.eps \
	sizes_graph.eps sizes_normal.eps time_graph.eps \
	tlb_graph.eps uop_graph.eps \
	ll_findstring_size.eps libc_sizes.eps \
	out.jgr out.eps out.png *.o new_graph \
	*.pdf *.aux *.dvi *.log *~
	
install:		       
			       scp ll_document.pdf vince@cluizel:public_html