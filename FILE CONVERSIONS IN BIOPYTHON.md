```python
#Vieing a gen bank file
from Bio import SeqIO
with open("sequence.gb") as input_handle:
    for record in SeqIO.parse(input_handle,"genbank"):
        print(record)
```

    ID: AH006904.2
    Name: AH006904
    Description: Theileria parva strain Muguga mitochondrion sequence
    Number of features: 7
    /molecule_type=DNA
    /topology=linear
    /data_file_division=INV
    /date=25-AUG-2016
    /accessions=['AH006904', 'AF046926', 'AF046927']
    /sequence_version=2
    /keywords=['']
    /source=mitochondrion Theileria parva
    /organism=Theileria parva
    /taxonomy=['Eukaryota', 'Sar', 'Alveolata', 'Apicomplexa', 'Aconoidasida', 'Piroplasmida', 'Theileriidae', 'Theileria']
    /references=[Reference(title='A 7.1 kb linear DNA molecule of Theileria parva has scrambled rDNA sequences and open reading frames for mitochondrially encoded proteins', ...), Reference(title='Telomeric features of Theileria parva mitochondrial DNA derived from cycle sequence data of total genomic DNA', ...), Reference(title='Direct Submission', ...)]
    /comment=On or before Aug 25, 2016 this sequence version replaced
    AF046927.1, AF046926.1, AH006904.1.
    Seq('AATTTATAACTTAAACTTCTTAACGACCAACAAATATATGTCTGAATTTAACGA...TGT')
    


```python
#Converting it to a fasta file

glosh = SeqIO.convert("sequence.gb","genbank","T.parva.fasta","fasta")
print("converted %i records" % glosh)
glosh


```

    converted 1 records
    




    1




```python
#viewing the converted file

with open("T.parva.fasta") as input_handle:
    for record in SeqIO.parse(input_handle,"fasta"):
        
        print(record)
```

    ID: AH006904.2
    Name: AH006904.2
    Description: AH006904.2 Theileria parva strain Muguga mitochondrion sequence
    Number of features: 0
    Seq('AATTTATAACTTAAACTTCTTAACGACCAACAAATATATGTCTGAATTTAACGA...TGT')
    


```python
#Vieing a fasta file
from Bio import SeqIO
with open("sequence(1).fasta") as input_handle:
    for record in SeqIO.parse(input_handle,"fasta"):
        print(record)
```

    ID: AY892288.1
    Name: AY892288.1
    Description: AY892288.1 Synthetic construct Homo sapiens clone FLH014428.01L TAR (HIV) mRNA, partial cds
    Number of features: 0
    Seq('ATGAGTGAAGAGGAGCAAGGCTCCGGCACTACCACGGGCTGCGGGCTGCCTAGT...TTG')
    


```python
#Converting the fasta file to genbank format

record = SeqIO.read("sequence(1).fasta","fasta")
record.annotations["molecule_type"] = "DNA"
SeqIO.write(record,"Humanclone.gb","gb")
```




    1




```python
#Viewing the converted file

with open("Humanclone.gb") as input_handle:
    for record in SeqIO.parse(input_handle,"genbank"):
        print(record)
    
```

    ID: AY892288.1
    Name: AY892288.1
    Description: AY892288.1 Synthetic construct Homo sapiens clone FLH014428.01L TAR (HIV) mRNA, partial cds
    Number of features: 0
    /molecule_type=DNA
    /data_file_division=UNK
    /date=01-JAN-1980
    /accessions=['AY892288']
    /sequence_version=1
    /keywords=['']
    /source=
    /organism=.
    /taxonomy=[]
    Seq('ATGAGTGAAGAGGAGCAAGGCTCCGGCACTACCACGGGCTGCGGGCTGCCTAGT...TTG')
    
