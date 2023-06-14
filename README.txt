#després d'obtenir la taula d'associació del DGenies l'haurem de modificar per introduir-la al Circos, a partir d'aquestes comandes obtindrem el cariotip de les dues espècies i el fitxer de links

transformar archivo dgenies para circos: sed 1d GCF_900880675.1_fSpaAur1.1_genomic_GCF_904848185.1_fAcaLat1.1_genomic_assoc.tsv  aurata_latus.txt
cut -f1,4 GCF_900880675.1_fSpaAur1.1_genomic_GCF_904848185.1_fAcaLat1.1_genomic_assoc.tsv | sed 1d | sort | uniq -c | wc -l #primer tallar columnes, després eliminem primera fila, sort es endreçar, uniq agafa elements unics (si poses -c te'ls conta),wc -l és contar el número de línies 
gunzip -c GCF_900880675.1_fSpaAur1.1_genomic.fna.gz | grep '>' | wc -l # despues de visualizar hacemos el grep, te selecciona las lineas que contienen elemento
gunzip -c GCF_900880675.1_fSpaAur1.1_genomic.fna.gz | grep '>' | grep 'chromosome' | wc -l: contar cuantos cromosomas hay en el fasta
cut -f2,7 GCF_900880675.1_fSpaAur1.1_genomic_GCF_904848185.1_fAcaLat1.1_genomic_assoc.tsv | sed 1d | sort | uniq >cariotip.latus.csv: acabar creando fichero target
cut -f1,4 GCF_900880675.1_fSpaAur1.1_genomic_GCF_904848185.1_fAcaLat1.1_genomic_assoc.tsv | sed 1d | sort | uniq >cariotip.aurata.csv: acabar creando fichero query
cat cariotip.aurata.csv cariotip.latus.csv > cariotip.aurata-latus.csv: unir los dos excel
grep -v 'NW' GCF_900880675.1_fSpaAur1.1_genomic_GCF_904848185.1_fAcaLat1.1_genomic_assoc.tsv > prova1.txt: -v per treure el que busques entre cometes
