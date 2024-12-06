# Lab class 6 10-18-24
Eli Sobel A69027989

## Quarto

Quarto enables you to weave together content and executable code into a
finished document. To learn more about Quarto see <https://quarto.org>.

## Running Code

When you click the **Render** button a document will be generated that
includes both content and the output of embedded code. You can embed
code like this:

``` r
add<-function(x,y){x+y}
add(4,8)
```

    [1] 12

``` r
add(3,1)
```

    [1] 4

``` r
add(c(100,1,100),1)
```

    [1] 101   2 101

# Make a function “generate_DNA()” that makes a random nucleotide sequence of any length.

``` r
# generate_DNA<-function()
bases<-c("A","C","G","T")

sequence<-sample(x=bases,size=1,replace=TRUE,prob=NULL)

generate_DNA<-function(length){
  bases<-c("A","C","G","T")
  sequence<-sample(bases,size=length,replace=TRUE,prob=NULL)
  return(sequence)
}
generate_DNA(9)
```

    [1] "G" "T" "A" "T" "C" "A" "T" "A" "A"

# make a function that can generate random protein sequences of a given length

# install.packages(“bio3d”)

``` r
generate_protein<-function(length){
  aa<-unique(bio3d::aa.table$aa1)
  seq<-sample(aa,size=length,replace=TRUE)
  seq<-paste(seq, collapse="")
  return(seq)
}
generate_protein(2)
```

    [1] "YA"

``` r
# generate protein sequences of length 6-13

answer<-sapply(6:12,generate_protein)
answer
```

    [1] "LKYKVT"       "AWECVQI"      "MAFIVCMI"     "QSIFLYNYA"    "VYNYKLTPAE"  
    [6] "XFRKCKSSXWQ"  "WWFHTVQVIXNX"

# generate FASTA formats for these sequences

``` r
cat(paste(">id",6:12,"\n",answer,sep=""), sep="\n")
```

    >id6
    LKYKVT
    >id7
    AWECVQI
    >id8
    MAFIVCMI
    >id9
    QSIFLYNYA
    >id10
    VYNYKLTPAE
    >id11
    XFRKCKSSXWQ
    >id12
    WWFHTVQVIXNX
