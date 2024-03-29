# A Durable Anti-Cancer Approach?
In 2012, three leading telomere biologists proposed a potentially universal anticancer approach: telomere maintenance mechanism (TMM) inhibition (Shay 2012). Telomeres shorten with every cell division eventually leading to cellular senescence. 85-90% of cancers use telomerase to extend telomeres and most normal cells do not express telomerase. Anti-telomerase cancer therapies have been in the literature for at least a decade (Suda 2002), so that alone isn't inherently interesting. The unique aspect of this 2012 Science article is the inclusion of the alternative lengthening of telomeres (ALT) mechanism as part of the inhibition scheme.

![Shay_Inhibiting_ALT_and_TEL](/Assets/Shay_Inhibiting_ALT_and_TEL.jpg "Shay_Inhibiting_ALT_and_TEL")

(Shay 2012)

It is estimated that 10-15% of cancers use ALT, a homologous recombination-based telomere extension mechanism (Cesare 2010). These ALT cancers would likely not respond to anti-telomerase therapies. Additionally, it has been reported that TEL cancers can switch to ALT and that some tumors may contain both ALT and TEL cancer cells. There are plenty of anti-telomerase clinical trials (Harley 2008), but there has been very little progression with ALT. The Science article calls for more ALT research and specifically for further development of ALT tests, like the C-circle assay (Shay 2012).

The lack of ALT research progress was what inspired me to spend five years working as a Research Associate at the SENS Research Foundation. I helped co-create a high-throughput version of the [the C-circle assay](https://patents.google.com/patent/WO2015179557A1/en), which Jeremy Henson is now using to [screen for ALT inhibitors](https://research.unsw.edu.au/people/dr-jeremy-david-henson). **In this repository I have reviewed the telomere literature to address problems not covered in the 2012 Science article:**

* Anti-Telomerase Therapy Causes Stem Cell Telomere Shortening
* The Ever Shorter Telomere (EST) Phenotype *Will Not* Respond to TMM inhibition
* Anti-ALT Therapy Might Interfere with Stem Cell Telomeres OR the DNA Damage Response

**I have created mathematical models of telomeres in ALT and TEL and included small telomere-based bioinformatics projects. _Sections discussing introns, exons, or promoters are emboldened in the table of contents._**

# Table of Contents
* <a href="#Telomeres_Shorten_with_Age">Telomeres Shorten with Age</a>
	* <a href="#Simple_1_Telomere_Shortening_Model">Simple 1 Telomere Shortening Model</a>
	* <a href="#Simple_1_Telomere_Model_Damage_Checkpoint">Simple 1 Telomere Model & Damage Checkpoint</a>
	* <a href="#23_Telomere_Model">23 Telomere Model</a>
	* <a href="#Telomere_Length_is_Linearly_Related_to_Chromosome_Length">Telomere Length is Linearly Related to Chromosome Length</a>
	* <a href="#Modeling_WT_Telomere_Shortening">Modeling WT Telomere Shortening</a>
* <a href="#Telomere_Maintenance_Mechanism_Selection">Telomere Maintenance Mechanism Selection</a>
* <a href="#Telomerase_Extends_Telomeres">Telomerase Extends Telomeres</a>
	* <a href="#Model_of_Different_Telomerase_Levels">Model of Different Telomerase Levels</a>
	* <a href="#Modeling_the_Single_Stranded_G-rich_Tail">Modeling the Single Stranded G-rich Tail</a>
	* <a href="#Model_of_Inhibiting_Telomerase">Model of Inhibiting Telomerase</a>
* <a href="#Alternative_Lengthening_of_Telomeres">Alternative Lengthening of Telomeres</a>
	* <a href="#ALT_Telomeres_are_Long_and_Heterogenous">ALT Telomeres are Long and Heterogenous</a>
	* <a href="#ALT_Telomere_Shortening">ALT Telomere Shortening</a>
	* <a href="#ALT_Telomeres_Have_C_rich_Overhangs">ALT Telomeres Have C-rich Overhangs</a>
	* **<a href="#POT_1_Deficiency_Creates_ALT_C_Elegans_Strains">POT-1 Deficiency Creates ALT+ C. Elegans Strains</a>**
		* **<a href="#Multiple_Sequence_Alignment_of_pot_1_Genes">Multiple Sequence Alignment of pot-1 Genes</a>**
		* **<a href="#Multiple_Sequence_Alignment_of_pot_1_Proteins">Multiple Sequence Alignment of pot-1 Proteins</a>**
		* **<a href="#Displaying_pot_1_Open_Reading_Frames">Displaying pot-1 Open Reading Frames</a>**
		* **<a href="#Discussing_C_elegans_pot_1_Alternative_Splicing">Discussing C. elegans pot-1 Alternative Splicing</a>**
	* **<a href="#ATRX_Exon_Deletion_is_Common_in_ALT">ATRX Exon Deletion is Common in ALT</a>**
		* **<a href="#Getting_ATRX_DNA">Getting ATRX DNA</a>**
		* **<a href="#Removing_ATRX_Exons_2_29">Removing ATRX Exons 2-29</a>**
		* **<a href="#Sequence_Alignment_of_WT_ATRX_to_Mutant_ATRX">Sequence Alignment of WT ATRX to Mutant ATRX</a>**
	* <a href="#Variants_Repeats_are_Found_in_ALT_Telomeres">Variants Repeats are Found in ALT Telomeres</a>
	* **<a href="#TERT_Promoter_Compaction_is_Found_in_ALT">TERT Promoter Compaction is Found in ALT</a>**
		* **<a href="#Getting_The_hTERT_Sequence">Getting The hTERT Sequence</a>**
		* **<a href="#Obtaining_hTERT_WITH_the_CpG_Island_Region">Obtaining hTERT WITH the CpG Island Region</a>**
		* **<a href="#Analyzing_the_Alleged_CpG_Promoter_Region">Analyzing the Alleged CpG Promoter Region</a>**
	* <a href="#STN1_Mutation_Triggers_ALT_in_Yeast">STN1 Mutation Triggers ALT in Yeast</a>
		* <a href="#Obtaining_STN1_From_3_Yeast_Organisms">Obtaining STN1 From 3 Yeast Organisms</a>
		* <a href="#Attempt_to_Replicate_Lyer_2005_Figure_4">Attempt to Replicate Lyer 2005 Figure 4</a>
		* <a href="#Aligning_Human_Yeast_and_Frog_STN1">Aligning Human, Yeast, and Frog STN1</a>
* <a href="#Ever_Shorter_Telomeres">Ever Shorter Telomeres</a>
	* <a href="#Mild_Telomerase_Activity">Mild Telomerase Acitivty Can Keep Cancers Dividing Long Enough for Metastasis</a>
	* <a href="#Long_Initial_Telomere_Lengths">Long Initial Telomere Lengths Can Keep Cancers Dividing Long Enough for Metastasis</a>
* <a href="#Conclusion">Conclusion</a>
* <a href="#Citations">Citations</a>

<a name="Telomeres_Shorten_with_Age"></a>
# Telomeres Shorten with Age
Human telomeres are estimated to be 5,000 - 15,000 base pairs at birth (Sanders 2013, Blackburn 2001). The end replication problem shortens telomeres by approximately 50 bp with each round of cell division (Proctor 2002, Suda 2002, Hastie 1990). 

<a name="Simple_1_Telomere_Shortening_Model"></a>
#### Simple 1 Telomere Shortening Model
Here's a simple mathematical model for one telomere:

```r
# These variables are the starting point. The starting telomere length is 5000. 50 bp are lost / division. 
starting_length = 10000
current_length <- starting_length
bp_loss_per_division = 50
current_division <- 0
number_of_cells <- 1
# This simplified model divides until there are no telomeres left. We will shortly see why this is not the case. 
while(current_length > 0) {
  # There will be 200 divisions for this case. I don't want to overwhelm the screen, so I'm limiting to #1 and #s divisible by 20.
  if(current_division == 0) {
    print(paste("There are ", number_of_cells, " cells after ", current_division, " doublings with a telomere length of ", current_length, " bp."))
  }
  else if (current_division %% 20 == 0) {
    print(paste("There are ", number_of_cells, " cells after ", current_division, " doublings with a telomere length of ", current_length, " bp."))
  }
  # The cells double, the telomere length is shortened by 50 bp, and the new division is initiated.
  number_of_cells <- number_of_cells * 2
  current_length <- current_length - 50
  current_division <- current_division + 1
}
# Here's the final situation.
print(paste("There are ", number_of_cells, " cells after ", current_division, " doublings with a telomere length of ", current_length, " bp."))
```

Here are the last couple of lines of output:

```sh
[1] "There are  1  cells after  0  doublings with a telomere length of  10000  bp."
[1] "There are  1048576  cells after  20  doublings with a telomere length of  9000  bp."
[1] "There are  1099511627776  cells after  40  doublings with a telomere length of  8000  bp."
[1] "There are  1152921504606846976  cells after  60  doublings with a telomere length of  7000  bp."
[1] "There are  1.20892581961463e+24  cells after  80  doublings with a telomere length of  6000  bp."
[1] "There are  1.26765060022823e+30  cells after  100  doublings with a telomere length of  5000  bp."
[1] "There are  1.32922799578492e+36  cells after  120  doublings with a telomere length of  4000  bp."
[1] "There are  1.39379657490816e+42  cells after  140  doublings with a telomere length of  3000  bp."
[1] "There are  1.4615016373309e+48  cells after  160  doublings with a telomere length of  2000  bp."
[1] "There are  1.53249554086589e+54  cells after  180  doublings with a telomere length of  1000  bp."
[1] "There are  1.60693804425899e+60  cells after  200  doublings with a telomere length of  0  bp."
```

<a name="Simple_1_Telomere_Model_Damage_Checkpoint"></a>
#### Simple 1 Telomere Model & Damage Checkpoint
The situation is more complicated than that model. A DNA damage checkpoint will be triggered at around 5k bp. If cell cycle checkpoints are intact, the cell will senesce at around 5 kb. If oncogenic changes have occurred, the cell will divide until around 3k bp. The subtelomeric region is estimated to be between 2-4 kbp (Counter 1996). There will be genomic instability, which will lead to more mutations and eventual cell death UNLESS a telomere maintenance mechanism stabilizes the telomeres (Harley 2008, Shay 2012). 

![Harley_2008_Box1a](/Assets/Harley_2008_Box1a.jpg "Harley_2008_Box1a")


Here's that slightly more complicated model:

```r
# These variables are the starting point. The starting telomere length is 5000. 50 bp are lost / division. 
starting_length = 10000
current_length <- starting_length
bp_loss_per_division = 50
current_division <- 0
number_of_cells <- 1
mutations <- 0
dividing <- TRUE
# This simple model divides until senescence is reached. 
while(dividing) {
  # There will be 200 divisions for this case. I don't want to overwhelm the screen, so I'm limiting to #1 and #s divisible by 20.
  if(current_division == 0) {
    print(paste("There is one ", number_of_cells, " cell with a telomere length of ", current_length, " bp and ", mutations, " mutations."))
  }
  else if (current_division %% 20 == 0) {
    # Shay 2012 model uses 1 mutation / 20 divisions 
    mutations <- mutations + 1
    print(paste("There are ", number_of_cells, " cells after ", current_division, " doublings with a telomere length of ", current_length, " bp and ", mutations, " mutations."))
  }
  # cells senesce around a telomere length of 5000 bp Harley 2008 
  else if (current_length < 5000) {
    dividing <- FALSE
    print("This cell has senesced at a telomere length of 5,000 bp")
  }
  # The cells double, the telomere length is shortened by 50 bp, and the new division is initiated.
  number_of_cells <- number_of_cells * 2
  current_length <- current_length - 50
  current_division <- current_division + 1
}
```


Here are the last couple of lines of output:

```sh
[1] "There is one  1  cell with a telomere length of  10000  bp and  0  mutations."
[1] "There are  1048576  cells after  20  doublings with a telomere length of  9000  bp and  1  mutations."
[1] "There are  1099511627776  cells after  40  doublings with a telomere length of  8000  bp and  2  mutations."
[1] "There are  1152921504606846976  cells after  60  doublings with a telomere length of  7000  bp and  3  mutations."
[1] "There are  1.20892581961463e+24  cells after  80  doublings with a telomere length of  6000  bp and  4  mutations."
[1] "There are  1.26765060022823e+30  cells after  100  doublings with a telomere length of  5000  bp and  5  mutations."
[1] "This cell has senesced at a telomere length of 5,000 bp"
```

In the previous model we saw that 5 mutations occurred over 100 population doublings. I based this on an assumption from one of Jerry Shay's oncogenic models. Cellular senescence stopped the cells in my current model from developing more mutations. It is thought that 8-15 mutations are enough for a cell to become cancerous (Shay 2012).

![Shay_2012_Mutations_Cancer](/Assets/Shay_2012_Mutations_Cancer.jpg "Shay_2012_Mutations_Cancer")

<a name="23_Telomere_Model"></a>
#### 23 Telomere Model
But there isn't just one telomere! Human cells have 23 pairs of chromosomes, so lets limit the view to the total telomere length for 23 human chromosomes. We will dive into p and q arms in a later section. It's been reported that the DNA damage checkpoint will be triggered by the shortest telomere (Harley 2008) ... so you should be questioning the validity of this model! Don't worry, it's about to get a lot more complicated :) 

```r
# picking a length of 6000 bp for each chromosome
starting_lengths = as.list(rep(6000, 23))
chromosome_names <- c((1:22), "X")
barplot(as.numeric(starting_lengths), names.arg=chromosome_names, las=2, main ="Telomere Lengths", xlab="Chromosome", ylab="Telomere Lenghts (bp)", ylim=c(0,7000))
abline(h=5000, col="red", lwd=3)
abline(h=3000, col="black", lwd=3)
```

![23_Chromosome_Simple_Lengths](/Assets/23_Chromosome_Simple_Lengths.jpg "23_Chromosome_Simple_Lengths")

<a name="Telomere_Length_is_Linearly_Related_to_Chromosome_Length"></a>
#### Telomere Length is Linearly Related to Chromosome Length
A DNA damage checkpoint will get triggered by the shortest telomere (Harley 2008). So a better mathematical model would take into account the distribution of telomere lengths and each individual telomere's shortening. See table 1 of Suda 2002 for the estimated telomere lengths of chromosomes 1-22 for the GM130B cell line. It is a telomerase positive (TEL+) spontaneously immortalized lymphoblast line from a male human. 

```r
# Suda 2002 Table 1 chromosome size (megabases) telomere length (bp).
chromosome_lengths <- c(246, 202, 193, 184, 173, 160, 146, 125, 110, 103, 100, 93, 85, 81, 62, 67, 48, 52)
telomere_lengths <- c(5681, 4987, 5018, 4589, 4302, 4127, 3922, 3708, 4045, 3624, 3460, 3109, 3077, 3007, 2750, 2913, 2735, 2806)
# these should be 18 long cause that's how many rows Suda 2002 has
length(chromosome_lengths)
length(telomere_lengths)
# plot the relationship
plot(chromosome_lengths, telomere_lengths, main ="Telomere and Chromosome Lengths are Linearly Related", xlab="Chromosome Lengths (Mb)", ylab="Telomere Lenghts (bp)")
```

![telomere_chromosome_linear](/Assets/telomere_chromosome_linear.jpg "telomere_chromosome_linear")

Suda 2002 didn't determine the lengths of the sex chromosomes. I want to create a formula to estimate the telomere lengths of the sex chromosomes. Here's how I did a linear regression in R:

```r
# this is a linear regression of the variables
lm(telomere_lengths ~ chromosome_lengths)
```

```sh
Call:
lm(formula = telomere_lengths ~ chromosome_lengths)

Coefficients:
       (Intercept)  chromosome_lengths  
           1920.25               14.93  
```

Here's that same initial plot, but I have included the line of fit:

```r
# here I'm using abline to add the line of regression
plot(chromosome_lengths, telomere_lengths, main ="Telomere Lengths are Linearly Related to Chromosome Lengths", xlab="Chromosome Lengths (Mb)", ylab="Telomere Lenghts (bp)")
abline(1920.25, 14.93)
```

![line_of_fit_chromosome_telomere](/Assets/line_of_fit_chromosome_telomere.jpg "line_of_fit_chromosome_telomere")

```r
# I'm assuming that this relationship will hold true for chromosomes X + Y
# AND that p/q is 1 in telomerase (Perrem 2001) 
# Morton 1991 Parameters has lengths of each chromosome, BUT, keep in mind that the chromosome Mb are slightly different from Suda 2002
chromosome_X_length <- 14.93*164 + 1920.25
chromosome_Y_length <- 14.93*59 + 1920.25
# Suda 2002 used a FACS technique that couldn't differentiate these chromosomes 1=2, 9=10=11=12
# I have assumed that their lengths are close enough (cause they're chromosomes are close in length)
chromosome_1_length <- telomere_lengths[1]
chromosome_2_length <- telomere_lengths[1]
chromosome_9_length <- telomere_lengths[8]
chromosome_10_length <- telomere_lengths[8]
chromosome_11_length <-telomere_lengths[8]
chromosome_12_length <- telomere_lengths[8]
# this could've been done more delicately, lol
# here's the complete list of lengths for autosomal chromosomes 1-22 and sex chromosomes x and y
chrom_1 <- chromosome_1_length
chrom_2 <- chromosome_2_length
chrom_3 <- telomere_lengths[2]
chrom_4 <- telomere_lengths[3]
chrom_5 <- telomere_lengths[4]
chrom_6 <- telomere_lengths[5]
chrom_7 <- telomere_lengths[6]
chrom_8 <- telomere_lengths[7]
chrom_9 <- chromosome_9_length
chrom_10 <- chromosome_10_length
chrom_11 <- chromosome_11_length
chrom_12 <- chromosome_12_length
chrom_13 <- telomere_lengths[9]
chrom_14 <- telomere_lengths[10]
chrom_15 <- telomere_lengths[11]
chrom_16 <- telomere_lengths[12]
chrom_17 <- telomere_lengths[13]
chrom_18 <- telomere_lengths[14]
chrom_19 <- telomere_lengths[15]
chrom_20 <- telomere_lengths[16]
chrom_21 <- telomere_lengths[17]
chrom_22 <- telomere_lengths[18]
chrom_X <- chromosome_X_length
chrom_Y <- chromosome_Y_length
# I should've just gone with chromosome X OR Y cause I'm only using one representative of the chromosomes 1-22
# BUT, I like how the bar graph looks this way :)
telomerase_chromosome_lengths <- c(chrom_1, chrom_2, chrom_3, chrom_4, chrom_5, chrom_6, chrom_7, chrom_8, chrom_9, chrom_10, chrom_11, chrom_12,chrom_13,chrom_14,chrom_15,chrom_16,chrom_17,chrom_18,chrom_19,chrom_20, chrom_21, chrom_22, chrom_X, chrom_Y)
# here are the labels for the chromosomes that I'm using 
telomerase_chromosome_names <- c((1:22), "X", "Y")
# and finally the barplot
barplot(telomerase_chromosome_lengths, names.arg=telomerase_chromosome_names, las=2, main ="GM130B Telomere Lengths", xlab="Chromosome", ylab="Telomere Lenghts (bp)", ylim=c(0,6000))
```

![GM130B_Telomere_Lengths](/Assets/GM130B_Telomere_Lengths.jpg "GM130B_Telomere_Lengths")

Suda 2002 estimated that the GM130B cell line could divide somewhere between 15 and 42 times. Here's how they arrived at that conclusion:

1) Identify the shortest and average telomere lengths
	* chromosome 21 is 2735 bp
2) Identify the average telomere lengths
	* They claim it's 3998 bp (It's actually 3770 bp ... check their math)
3) Subtract the 2000 bp subtelomeric region
	* chromosome 21 is down to 735 bp and the average is down to 1998 bp
4) Divide those bp numbers by the bp lost/division
	* chromosome 21 735/48 = 15.3 PD & 1998/48=41.6 PD

It's well-established nowadays that the shortest telomere is what determines when cellular senescence will start. Here's a model of the short telomere cellular senescence model from Suda 2002:

```r
# this is the condition that, while TRUE, runs the model
above_zero <- TRUE
division_number <- 0
# assuming subtelomere is 2000 bp
telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths - 2000
while(above_zero) {
  barplot(telomerase_chromosome_lengths_play, names.arg=telomerase_chromosome_names, las=2, main = paste("GM130B Senescence After ", division_number, " Divisions"), xlab="Chromosome", ylab="Telomere Lenghts (bp)", ylim=c(0,3000))
  telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_play - 48
  division_number <- division_number + 1
  if(sum((telomerase_chromosome_lengths_play) < 0) > 0) {
    above_zero <- FALSE
  }
}
```

Here's that final senescent state:

![GM130B_Senesces_After_15PD](/Assets/GM130B_Senesces_After_15PD.jpg "GM130B_Senesces_After_15PD")

<a name="Modeling_WT_Telomere_Shortening"></a>
#### Modeling WT Telomere Shortening
The Suda 2002 is a very interesting case with an immortalized cell. This is my attempt to model the initial telomere length state for a human at birth and follow it through until senescence. Note that I'm using the Harley 2008 5 kb red line of senescence and the black 3kb line of crisis.

```r
# I wanna make sure that I don't change the length list that I created earlier
telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths
# the range of telomere lengths from GM130B is 2946
max(telomerase_chromosome_lengths_play) - min(telomerase_chromosome_lengths_play)
# scaling that range up to 10000 bp with multiplication yields a range of 5185
telomerase_chromosome_lengths_START <- telomerase_chromosome_lengths * 10000/max(telomerase_chromosome_lengths)
max(telomerase_chromosome_lengths_START) - min(telomerase_chromosome_lengths_START)
# 5185 bp seemed a bit high for the range (just intuition), so I used an additive instead
telomerase_chromosome_lengths_START <- telomerase_chromosome_lengths + 10000 - max(telomerase_chromosome_lengths)
max(telomerase_chromosome_lengths_START) - min(telomerase_chromosome_lengths_START)

# How long till senescence if starting max is 10K AND maintaining telomere length range of GM130B?
above_five_thousand <- TRUE
division_number <- 0
telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_START
while(above_five_thousand) {
  #print(telomerase_chromosome_lengths_play)
  #print(division_number)
  barplot(telomerase_chromosome_lengths_play, names.arg=telomerase_chromosome_names, las=2, main = paste("hCell Telomere Shortening After ", division_number, " Divisions"), xlab="Chromosome", ylab="Telomere Lenghts (bp)", ylim=c(0,10000))
  abline(h=5000, col="red", lwd=3)
  abline(h=3000, col="black", lwd=3)
  division_number <- division_number + 1
  telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_play - 48
  if(sum(telomerase_chromosome_lengths_play < 5000) > 0) {
    above_five_thousand <- FALSE
  }
}
```

Here's the initial state:
![hCell_Shortening_After_0_Divisions](/Assets/hCell_Shortening_After_0_Divisions.jpg "hCell_Shortening_After_0_Divisions")

This model divided 42 times before senescing.

![hCell_Shortening_After_42_Divisions](/Assets/hCell_Shortening_After_42_Divisions.jpg "hCell_Shortening_After_42_Divisions")


<a name="Telomere_Maintenance_Mechanism_Selection"></a>
# Telomere Maintenance Mechanism (TMM) Selection
The selection of TMM seems to mainly depend upon telomerase chromatin compaction and mutations in ATRX & p53 (Gocha 2013). 
 
![ALT_TEL_Permissive_Mutations](/Assets/ALT_TEL_Permissive_Mutations.jpg "ALT_TEL_Permissive_Mutations")

(Gocha 2013)

<a name="Telomerase_Extends_Telomeres"></a>
# Telomerase Extends Telomeres
Telomerase adds 5'-GGTTAG-3' (Harley 2008). Telomerase extends the shortest telomeres first (Harley 2008, Cristofari 2006). The G-rich strand is 5'-GGTTAG-3' and the C-rich strand is 3'-CCAATC-5'. Telomerase adds 5'-GGTTAG-3' (Harley 2008). The telomerase enzyme TERT uses the telomerase RNA 3'-CAAUCCCAAUC-5' as a template for the extension (Gavory 2002). There is a G-rich single stranded telomeric overhang of 130-210 nucleotides (Cesare 2010). telomerase, which is a reverse transcriptase that adds repetitive telomeric DNA (TTAGGG)n to the ends of the chromosomes (Allsopp 2001). 

<a name="Model_of_Different_Telomerase_Levels"></a>
#### Model of Different Telomerase Levels
Telomerase overexpression might have an upper limit of 0.8 kb/division ... I'm not certain, but that was reported in Cristofari 2006. I might want to create a future update that limits to 800 bases/division just to keep cellular resources in mind. I don't know how model the telomerase activity in Python with a great deal of biological accuracy ... 

1. How much RNA template is available?
2. How long will a telomerase enzyme be active?
3. How do you model 3-D interactions?
etc.,

so I've decided to simplify the telomerase model to adding back the 48 bp lost HALF of the time. Harley 2008 box 1b (below) was the inspiration of this idea, but keep in mind that things are WAY more complicated than this. Yes, it's a spherical cow kind of model, but what could I do better? Seriously, message me if you've got an idea, cause I'll try it out :) 

![Harley_2008_box1b](/Assets/Harley_2008_box1b.jpg "Harley_2008_box1b")

```r
# How long till senescence if starting max is 10K AND maintaining telomere lengths of GM130B?
# AND telomerase is periodically turned on? AND senescence checkpoints work.
# Telomerase extends the shortest telomeres first (Harley 2008, Cristofari 2006)
# I'm not worried about that when telomere shortening overpowers telomere lengthening
above_five_thousand <- TRUE
division_number <- 0
telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_START
while(above_five_thousand) {
  #print(telomerase_chromosome_lengths_play)
  #print(division_number)
  barplot(telomerase_chromosome_lengths_play, names.arg=telomerase_chromosome_names, las=2, main = paste("Trasient Telomerase Telomere Shortening After ", division_number, " Divisions"), xlab="Chromosome", ylab="Telomere Lenghts (bp)", ylim=c(0,10000))
  abline(h=5000, col="red", lwd=3)
  abline(h=3000, col="black", lwd=3)
  division_number <- division_number + 1
  telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_play - 48
  if(division_number %% 2){
    telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_play + 48
  }
  if(sum(telomerase_chromosome_lengths_play < 5000) > 0) {
    above_five_thousand <- FALSE
  }
  # this indicates immortality and I don't want a runaway while loop
  if(division_number > 100) {
    break
  }
}
```

![Transient_Telomerase_HSC](/Assets/Transient_Telomerase_HSC.jpg "Transient_Telomerase_HSC")


This is when telomerase is equal to the telomere shortening.

```r
# what about a cancer with telomerase always turned on?
# telomerase + cells still have the trimming mechanism turned on
# Pickett 2009  HT1090 +TEL stuck at 7.5 kb, HeLa stuck at 4.5 kb
# overexpression of hTER HeLa 8 kb, HT1080 hTR increasingly heteogenous 9.4 kb
# I could make a complicated function to make sure things stay matched, but you get the idea ...
# I'll just make shortening equal to lengthening
above_five_thousand <- TRUE
division_number <- 0
telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_START
while(above_five_thousand) {
  #print(telomerase_chromosome_lengths_play)
  #print(division_number)
  barplot(telomerase_chromosome_lengths_play, names.arg=telomerase_chromosome_names, las=2, main = paste("Immortalized Telomerase Telomere Shortening After ", division_number, " Divisions"), xlab="Chromosome", ylab="Telomere Lenghts (bp)", ylim=c(0,10000))
  abline(h=5000, col="red", lwd=3)
  abline(h=3000, col="black", lwd=3)
  division_number <- division_number + 1
  telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_play - 48
  telomerase_chromosome_lengths_play <- telomerase_chromosome_lengths_play + 48
  if(sum(telomerase_chromosome_lengths_play < 5000) > 0) {
    above_five_thousand <- FALSE
  }
  # this indicates immortality and I don't want a runaway while loop
  if(division_number > 300) {
    break
  }
}
```

Note that the code breaks at 300 population doublings because it'd go on forever otherwise. Telomerase does seem to have an upper limit for the telomere lengths that are possible. Picket 2009 found that HeLa and HT1080 stayed at 4.5 and 7 kbp under normal telomerase conditions, BUT that they went up to 8 and 9.4 kbp with hTR overexpression. There appears to be a natural telomere trimming mechanism under normal conditions (Picket 2009).

![Immortalized_Telomerase](/Assets/Immortalized_Telomerase.jpg "Immortalized_Telomerase")

<a name="Modeling_the_Single_Stranded_G"></a>
#### Modeling the Single Stranded G-rich Tail
Another thing that I left out of earlier models was the G-rich and C-rich strands. I've just been describing the telomeres as having a length. They have sequence too! The G-rich strand is 5'-GGTTAG-3' and the C-rich strand is 3'-CCAATC-5'. Telomerase adds 5'-GGTTAG-3' (Harley 2008). The telomerase enzyme TERT uses the telomerase RNA 3'-CAAUCCCAAUC-5' as a template for the extension (Gavory 2002). There is a G-rich single stranded telomeric overhang of 130-210 nucleotides (Cesare 2010).

I made a simple model of the G'rich overhang in R.

```r
setwd("/media/david/Linux/ALT_Introns_Exons_and_Promoters/Telomere_Math_Models")
library(msa)
library(seqinr)
G_overhang_sequence <- "GGTTAG"
C_overhang_sequence <- "CCAATC"
reverse_complement_C_overhang_sequence <- "CTAACC"
# 22*6 = 132 (min single stranded overhang is 130)
# assuming 10 kbp telomere lengths, so 1666 * 6 9996 is for C strand
# then 1666+22 is for G strand
full_G_overhang_sequence <- paste(replicate(1688, G_overhang_sequence), collapse = "")
full_C_overhang_sequence <- paste(replicate(1666, reverse_complement_C_overhang_sequence), collapse = "")
write.fasta(sequences = full_G_overhang_sequence, names = "full_G_overhang_sequence", file.out = "full_G_overhang_sequence.fasta", open = "w", nbchar = 70, as.string = FALSE)
write.fasta(sequences = full_C_overhang_sequence, names = "full_C_overhang_sequence", file.out = "full_C_overhang_sequence.fasta", open = "w", nbchar = 70, as.string = FALSE)
```

I can't figure out how to make a pretty DNA complementary base pairing figure ... any ideas? Please let me know :) I made a simple, shortened, text version:

![G_overhang](/Assets/G_overhang.jpg "G_overhang")

NOTE: I NEED TO MAKE SURE I'VE GOT THE RIGHT NUMBER FOR TELOMERE VS. SUBTELOMERE ... CHECK RESTRICTION ENZYME DATA AND READ THESE TWO PAPERS: 
Riethman 2004 Mapping and Initial Analysis of Human Subtelomeric Sequence Assemblies
Riethman 2009 Human subtelomeric copy number variations
Mefford 2002 The complex structure and dynamic evolution of human subtelomeres
Suda 2002 Interchromosomal Telomere Length Variation
Graakjaer 2003 The pattern of chromosome-specific variations in telomere length in humans is determined by inherited, telomere-near factors and is maintained throughout life

<a name="Model_of_Inhibiting_Telomerase"></a>
#### Model of Inhibiting Telomerase 
When DNA is getting copied, small end pieces aren't able to be fully copied. This is known as the End Replication Problem and is a result of Okazaki fragments incompletely covering the end of the chromosome. This is an issue for cell types that need to divide a lot, like Hematopoietic stem cells (HSC). HSCs have plenty of division to do so they can keep up with all the differentiation to make blood cells. This is why they express telomerase, which is a reverse transcriptase that adds repetitive telomeric DNA (TTAGGG)n to the ends of the chromosomes (Allsopp 2001). Did you notice that I'm citing a paper from the Weissman lab? ;)  
 
![telomeres-shorten-with-age](/Assets/telomeres-shorten-with-age.jpg "telomeres-shorten-with-age")

(Finkel 2007)

Cells that divide a lot will senesce in the absence of an active telomere maintenance mechanism (Shay 2012). That's why Telomerase is great for stem cells and other cell types that need to divide a lot. HOWEVER, it's also part of how the majority of cancers become immortal (Cesare 2010). This is why several companies are working on telomere-based anti-cancer therapies:

* Telomerase enzyme inhibitor: 
	* GRN163L (Geron)
* Telomerase active immunotherapy:	
	* GRNVAC1 (Geron)
	* GV1001 (Pharmexa)
	* P540-548 (Gemvax)
	* Vx01 (Vaxon Biotech)
	* TLI (Cosmo Bioscience) 

(Shay 2012, Harley 2008)

This model is the same as the telomere shortening + telomerase model AND you can choose a cell division number for telomerase to be inhibited at. There are two scenarios that I want to model:

1) cancers with relatively short telomeres (these will divide out without telomerase)
2) cancers with very long telomeres (these might be able to keep dividing in the absence of telomerase)
3) cancers with telomeres that are equilavent to stem cell telomeres (anti-telomerase therapy will exhaust the stem cell pools before the cancer)

I bring up point 3 because one problem with telomerase inhibitors is that they have been reported to cause problems with blood stem cells (Hu 2017). This update only needed three lines of code. I added a varible for the division number for telomerase to stop at and an if condition that sets telomerase activity to 0 AFTER that division number has been reached. 

```r
I NEED TO FINISH MAKING THIS
```

<a name="Alternative_Lengthening_of_Telomeres"></a>
# Alternative Lengthening of Telomeres (ALT) Extends Telomeres
Stem cell telomerase isn't the only problem with the telomerase inhibition approach. Approximately 10-15% of cancers use the Alterantive Lengthening of Telomeres (ALT) to extend telomeres, some cancers won't be treated with these anti-telomerase therapies. But, it's way worse of a problem than that! Tumors have been reported to use both ALT and TEL simultaneously (Gocha 2013) AND in vitro inhibition of telomerase selects for ALT activity (Sahin 2012). 

![TEL_ALT_Reversible](/Assets/TEL_ALT_Reversible.jpg "TEL_ALT_Reversible")

(Shay 2012)

On an interesting note, there is a high frequency of cancers with a Mesenchymal Stem Cell origin using the ALT pathway (77% malignant fibrous histocytomas, 47-66% of osteosarcomas (Lafferty-Whyte 2009), 21.4% of liposarcomas (Venturini APB ALT LIPOSARCOMA 2008). This may be a result of the telomerase promoter being repressed with chromatin compaction (Atkinson 2005). Telomerase inhibition MIGHT not be alone in potentially causing problems for stem cells. There is some evidence to suggest that stem cells use ALT (Kalmbach 2014, Huang 2014). To make things worse, some cancers appear to extensively divide without a telomere maintenance mechanism (Dagg 2017).  

![stem_cell_ALT.jpg](/Assets/stem_cell_ALT.jpg "stem_cell_ALT.jpg")

(Kalmbach 2014)

<a name="ALT_Telomeres_are_Long_and_Heterogenous"></a>
#### ALT Telomeres are Long and Heterogenous
ALT telomeres have long, heterogenous telomeres. They can range from less than 1 kbp (Rogan 1995) all the way up to 50 kbp (Bryan 1995). There is a rapid addition of telomeric sequences to short telomeres AND a rapid deletion of telomeric sequences from the long telomeres. This suggests recombinogenic behavior (Murnane 1994). ALT cells seem to be extending their telomeres through this process, but the mechanism isn't completely understood yet (Cesare 2010). There are common losses and duplications of chromosomes (Sakellariou 2013). The ratio of p/q telomeric arms range from 10-0.1.

I think there are still more details that I should take into account for this idea, but I'm not sure when I'll have the time for that. The simplified model I have in mind will:

1) range in initialized telomere length from 500 bp to 50,000 bp
2) have a p/q telomeric arm ratio betwen 10-0.1
3) take the 92 different telomere endings into account

Forgive me for not representing actual ALT activity. It was pretty tough just getting the code to inititate ALT telomeres!

```r
# it creates 92 telomeres
ALT_telomere_lengths <- vector("list", 92)
# these are placeholders for values that will be used throughout the program
current_telomere_length_total <- 0
current_telomere_length_Q <- 0
current_telomere_length_P <- 0
list_of_PQ_ratios <- vector("list", 46)
text_of_PQ_numbers <- vector("list", 46)
# i keeps track of the current interation. Note that each run has two iterations of adding to the tel length list
i <- 1
j <- 1
generate_ALT_telomeres <- function() {
  # runs for 46 items (cause 92 total and creating p and q w/ each loop)
  for(length in 1:46){
    # determine the total telomere length between 500 and 50,000 bp
    #current_telomere_length <- runif(1, min=500, max=50000)
    #current_telomere_length <- rnorm(1, 15000, 2000)
    # current_telomere_length <- rnorm(1, 20000, 1250) + runif(1, min=500, max=20000)
    current_telomere_length <- runif(1, min=10000, max=50000)
    # determine the p/q ratio between 0.1 and 10
    P_to_Q_ratio <- runif(1, -10, 10)
    if(P_to_Q_ratio == 1) {
      current_telomere_length_P <- current_telomere_length * 0.5
      current_telomere_length_Q <- current_telomere_length * 0.5
    } else if(P_to_Q_ratio > 1) {
      # P_to_Q_ratio <- runif(1, 0.1, 10)
      current_telomere_length_Q <- current_telomere_length/(runif(1, 0.1, 10)+1)
      current_telomere_length_P <- current_telomere_length - current_telomere_length_Q
    } else if(P_to_Q_ratio < 1) {
      current_telomere_length_P <- current_telomere_length/(runif(1, 0.1, 10)+1)
      current_telomere_length_Q <- current_telomere_length - current_telomere_length_P
    }
    # current_telomere_length_P <- current_telomere_length - current_telomere_length_Q
    # get the sum (this number is already known. I'm using it for error checking)
    current_sum_p_q <- current_telomere_length_Q+current_telomere_length_P
    # get the p/q ratio (this number is already known. I'm using it for error checking)
    determine_P_to_Q_ratio <- current_telomere_length_P / current_telomere_length_Q
    list_of_PQ_ratios[j] <- determine_P_to_Q_ratio
    text_of_PQ_numbers[j] <- paste("P is ", current_telomere_length_P, " Q is ", current_telomere_length_Q)
    # print out the math to check by hand
    #print(paste("current total length is ", current_telomere_length, "Q is ", current_telomere_length_Q, "P is ", current_telomere_length_P, " sum is ", current_sum_p_q))
    #print(paste("current P_to_Q_ratio is ", P_to_Q_ratio, "Q is ", current_telomere_length_Q, "P is ", current_telomere_length_P, " P_to_Q_ratio is ", determine_P_to_Q_ratio))
    #print("")
    # store current p and q arms
    ALT_telomere_lengths[i] <- current_telomere_length_P 
    i <- i + 1
    ALT_telomere_lengths[i] <- current_telomere_length_Q
    i <- i + 1
    
    j <- j + 1
  }
  #return(ALT_telomere_lengths)
  #return(list_of_PQ_ratios)
  newList <- list("lengths" = ALT_telomere_lengths, "ratios" = list_of_PQ_ratios, "text" = text_of_PQ_numbers)
  return(newList)
}
newList <- generate_ALT_telomeres()

ALT_telomere_lengths <- newList$lengths
list_of_PQ_ratios <- newList$ratios
text_of_PQ_numbers <- newList$text
#ALT_telomere_lengths <- generate_ALT_telomeres()
#list_of_PQ_ratios <- generate_ALT_telomeres()
```

Here is a logarithmic barplot of the P/Q ratios. I added a line at the P/Q=1 position.

![P_to_Q_Ratio](/Assets/P_to_Q_Ratio.jpg "P_to_Q_Ratio")

Here are those telomeres plotted as a bar graph:

```r
# This is a disgusting mess of overwhelming data
barplot(as.numeric(ALT_telomere_lengths), names.arg=autosome_pairs_sex_chromosomes_and_arms, las=2, main="ALT+ Telomere Lengths for Chromosomes", xlab="Chromosome", ylab="Telomere Lengths (bp)", ylim=c(0,50000))
abline(h=5000, col="red", lwd=3)
abline(h=3000, col="black", lwd=3)
```

Gosh! This looks terrible! The axes labels are covering over the telomere lengths AND the chromosome names. I'll need to tidy up ... actually, I'm just going to look at telomeres 1-46

![ALT_ugly_telomeres](/Assets/ALT_ugly_telomeres.jpg "ALT_ugly_telomeres")

```r
barplot(as.numeric(ALT_telomere_lengths[1:46]), names.arg=autosome_pairs_sex_chromosomes_and_arms[1:46], las=2, main="ALT+ Telomeres 1-46", ylab="Telomere Lengths (bp)", ylim=c(0,50000))
abline(h=5000, col="red", lwd=3)
abline(h=3000, col="black", lwd=3)
```

![ALT_telomeres_1_46](/Assets/ALT_telomeres_1_46.jpg "ALT_telomeres_1_46")

```r
barplot(as.numeric(ALT_telomere_lengths[47:92]), names.arg=autosome_pairs_sex_chromosomes_and_arms[47:92], las=2, main="ALT+ Telomeres 47-92", ylab="Telomere Lengths (bp)", ylim=c(0,50000))
abline(h=5000, col="red", lwd=3)
abline(h=3000, col="black", lwd=3)
```

![ALT_telomeres_47_92](/Assets/ALT_telomeres_47_92.jpg "ALT_telomeres_47_92")

<a name="ALT_Telomere_Shortening"></a>
#### ALT Telomere Shortening
If ALT is inhibited, telomeres may shorten at a rate of -175 bp/PD (Potts 2005).
```r
# Potts 2005 -175 bp / PD for inhibition of SMC5/6 complex. 36 PD for cellular senescence
play_ALT_telomere_lengths <- ALT_chromosome_lengths
dividing <- TRUE
divisions <- 0
while(dividing) {
  barplot(as.numeric(play_ALT_telomere_lengths), las=2, main=paste("ALT+ Telomere Lengths After ", divisions, "Divisions"), ylim=c(0,50000))
  abline(h=5000, col="red", lwd=3)
  abline(h=3000, col="black", lwd=3)
  play_ALT_telomere_lengths <- as.numeric(play_ALT_telomere_lengths) - 175
  #for(i in length(1:46)) {
  #  current_total <- 
  #}
  if (min(play_ALT_telomere_lengths) < 3000){
    dividing <- FALSE
  }
  divisions <- divisions + 1
}
```

![ALT_telomeres_after_45_divisions](/Assets/ALT_telomeres_after_45_divisions.jpg "ALT_telomeres_after_45_divisions")

<a name="ALT_Telomeres_Have_C_rich_Overhangs"></a>
#### ALT Telomeres Have C-rich Overhangs
There is some degree of 5' C-rich overhang in ALT cells. 

![C_overhang](/Assets/C_overhang.jpg "C_overhang")

^I need to do a bit more reading to make an accurate model of this. Here are some good papers to check out:

* Oganesian 2011 Mammalian 5 0 C-Rich Telomeric Overhangs Are a Mark of Recombination-Dependent Telomere Maintenance
* Min 2017 Alternative lengthening of telomeres can be maintained by preferential elongation of lagging strands
* Mao 2016 Homologous recombination-dependent repair of telomeric DSBs in proliferating human cells

The altered C-rich overhangs involved in ALT will likely prevent POT-1 from binding effectively to the telomeres. This is a great segway into the ALT literature! For example, POT-1 deficiency creates ALT in C. elegans!

<a name="POT_1_Deficiency_Creates_ALT_C_Elegans_Strains"></a>
#### POT-1 Deficiency Creates ALT+ C. Elegans Strains
Telomeres cap linear chromosomes because DNA polymerase can't completely copy chromosomes. Telomerase adds telomeric repeats to the ends of linear chromosomes with reverse transcription. Most human cancers have long, heterogenous telomeres. Telomere shortening leads to senescence and potentially crisis. Cancer emerges as part of massive cell death and genomic rearrangements after crisis. 10-15% of cancers are estimated to use ALT (Cheng 2012). 

ALT can happen in Caenorhabditis elegans! Mammalian POT1 has homologs in C. elegans as pot-1 (CeOB2) and pot-2 (CeOB1). What's the deal with the reversing of 1 and 2? That's how it's reported in the paper ... it's odd. pot-1 mutant C. elegans have HUGE telomere lengths while pot-2 mutants have normal telomere lengths. The authors of Cheng 2012 created a variety of mutants in C. elegans.  The trt-1 C. elegans mutant has a deletion in telomerase reverse transcriptase. trt-1 & pot-2 absence led to ALT+ Caenorhabditis elegans with normal telomere lengths. trt-1 and pot-1 mutants were found to have long, heterogenous telomere lengths like those seen in human ALT. Here is the survival figure showing that C. elegans can survive in the absence of telomerase reverse transcriptase.

![Celegans_ALT_Generation_Survival](/Assets/Celegans_ALT_Generation_Survival.jpg "Celegans_ALT_Generation_Survival")

(Cheng 2012)

<a name="Multiple_Sequence_Alignment_of_pot_1_Genes"></a>
###### Multiple Sequence Alignment of pot-1 Genes
YES, pot-2 was the central point of the paper, but it won't be as fun to play with because it only has one isoform. I picked pot-1 cause there is a lot of cool stuff to play with. There were a lot of workup steps to get all of the sequences ... It would take a long while to review them. Essentially, I looked up the proteins on UniProt and then grabbed the DNA files from NCBI GenBank and WormBase. Check out the Celegans_POT1_ALT folder for the file names of everything. The file containing all the C. elegans genes is Celegans_POT1_genes.fasta. I used the R package "msa" for multiple sequence alignment with this code:

```r
library(msa)
Celegans_POT1_genes <- "/media/david/Linux/Introns_Exons_and_Promoters/Celegans_POT1_ALT/DNA/Celegans_POT1_genes.fasta"
Celegans_POT1_genes_DNA <- readDNAStringSet(Celegans_POT1_genes)
Celegans_POT1_gene_alignment <- msa(Celegans_POT1_genes_DNA)
msaPrettyPrint(Celegans_POT1_gene_alignment, output="pdf", showNames="none",
showLogo="none", askForOverwrite=FALSE, verbose=FALSE)
```

The aligned sequences aren't very pretty ... I decided not to include sequence labels cause it shortened the available nucleotide space for each new line. Here's part of the output for you to get the idea of the work:

![Celegans_POT1_gene_alignment](/Assets/Celegans_POT1_gene_alignment.jpg "Celegans_POT1_gene_alignment")

<a name="Multiple_Sequence_Alignment_of_pot_1_Proteins"></a>
###### Multiple Sequence Alignment of pot-1 Proteins
I grabbed all the C elegans pot-1 isoform sequences from UniProt. You can check them out in Celegans_POT1_ALT/Protein. The file containing all of the sequences is Celegans_POT1_Proteins.fasta. I aligned all of the proteins with code that is similar to the DNA alignment code:

```r
Celegans_POT1_proteins <- "/media/david/Linux/Introns_Exons_and_Promoters/Celegans_POT1_ALT/Protein/Celegans_POT1_Proteins.fasta"
Celegans_POT1_proteins_AA <- readAAStringSet(Celegans_POT1_proteins)
Celegans_POT1_protein_alignment <- msa(Celegans_POT1_proteins_AA)
Celegans_POT1_protein_alignment
msaPrettyPrint(Celegans_POT1_protein_alignment, output="pdf", showNames="none",
showLogo="none", askForOverwrite=FALSE, verbose=FALSE)
```

This alignment looks great! You can see all of the alignments between the different pot-1 isoforms :)

![Celegans_POT1_protein_alignment](/Assets/Celegans_POT1_protein_alignment.jpg "Celegans_POT1_protein_alignment")

<a name="Displaying_pot_1_Open_Reading_Frames"></a>
###### Displaying pot-1 Open Reading Frames
I used code from the BioPython Tutorial to identify the C. elegans pot-1 gene Open Reading Frames AND to report the translated proteins! Compare this to the last section to see that the the DNA -> Protein translations all have the correct lengths! The code is from http://biopython.org/DIST/docs/tutorial/Tutorial.html in the section titled "20.1.13. Identifying open reading frames". You should check this code out! It can identify Open Reading Frames in the +/- strand AND in three different reading frames, SO IT DOES ALL 6 FRAMES!!! I re-used the code four times (instead of making a function, haha). Here's part of the code that I used:

```python
#!/usr/bin/env python

from Bio import SeqIO
# record = SeqIO.read("NC_005816.fna", "fasta")
file_0 = "NM_001361730.1_Caenorhabditis_elegans_pot-1_gene_homolog.fasta"
file_1 = "NM_001361731.1_Caenorhabditis_elegans_pot-1_gene_homolog.fasta"
file_2 = "NM_001361732.1_Caenorhabditis_elegans_pot-1_gene_homolog.fasta"
file_3 = "NM_066157.3_pot-1_NCBI_DNA_matchesP42001_Celegans.fasta"

print("")
print("NM_001361730.1_Caenorhabditis_elegans_pot-1_gene_homolog.fasta")
record = SeqIO.read(file_0, "fasta")
table = 11
min_pro_len = 150

for strand, nuc in [(+1, record.seq), (-1, record.seq.reverse_complement())]:
    for frame in range(3):
        length = 3 * ((len(record)-frame) // 3) #Multiple of three
        for pro in nuc[frame:frame+length].translate(table).split("*"):
            if len(pro) >= min_pro_len:
                print("%s...%s - length %i, strand %i, frame %i" \
                % (pro[:30], pro[-3:], len(pro), strand, frame))
```

![Displaying_pot-1_Open_Reading_Frames](/Assets/Displaying_pot-1_Open_Reading_Frames.jpg "Displaying_pot-1_Open_Reading_Frames")

<a name="Discussing_C_elegans_pot_1_Alternative_Splicing"></a>
###### Discussing C. elegans pot-1 Alternative Splicing
WormBase has three isoforms for pot-1 in C. elegans https://wormbase.org/species/c_elegans/gene/WBGene00015105#0-9g-3

![WormBase_pot-1_Celegans_Isoforms](/Assets/WormBase_pot-1_Celegans_Isoforms.jpg "WormBase_pot-1_Celegans_Isoforms")

Transcript B0280.10a.1 is 1216 nucleotides in length and codes for a 400 amino acid protien. The WormBase curators used RNA-seq data from Boeck 2016 to alter the original WormBase entry to include the published alternate intron splicing. You can see from the table that Exons 1-10 are part of this pot-1 isoform.

![B0280.10a.1_Celegans_pot-1_isoformA_1203NT_400AA](/Assets/B0280.10a.1_Celegans_pot-1_isoformA_1203NT_400AA.jpg "B0280.10a.1_Celegans_pot-1_isoformA_1203NT_400AA")

Transcript B0280.10b.1 is 462 nucleotides in length and it codes for a 153 amino acid protein. You can see from the table that Exons 1-4 are part of this pot-1 isoform. Boeck 2016 goes into more detail about the alternative intron that causes alternative splicing here. 

![B0280.10b.1_Celegans_pot-1_isoformB_462NT_153AA](/Assets/B0280.10b.1_Celegans_pot-1_isoformB_462NT_153AA.jpg "B0280.10b.1_Celegans_pot-1_isoformB_462NT_153AA")

Transcript B0280.10c.1 is 1140 nucleotides long and it codes for a 379 amino acid protein. You can see from the table that Exons 1-10 make it into this protein isoform.

![B0280.10c.1_Celegans_pot-1_isoformC_1140NT_379AA](/Assets/B0280.10c.1_Celegans_pot-1_isoformC_1140NT_379AA.jpg "B0280.10c.1_Celegans_pot-1_isoformC_1140NT_379AA")

<a name="ATRX_Exon_Deletion_is_Common_in_ALT"></a>
##### ATRX Exon Deletion is Common in ALT
This project can be found in the Human_ATRX_ALT folder. ATRX gene mutations are found in a range of cancers. 10-15% of cancers are estimated to use ALT. ALT involves homologous recombination-based telomere elongation. Inactivating mutations in either ATRX or DAXX are found in many cancers. Depletion of ATRX seems insufficient to trigger ALT, but it does seem to play a key role in the ALT pathway. The absence of ATRX might lead to the failure of stalled replication forks to get resolved. The required fork restart would require homologus recombination and could jumpstart the ALT pathway (Clynes 2013). ALT involves a template-based lengthening of telomeres with homologous recombination. The genetic and epigenetic changes are not full understood. Lovejoy 2012 reported that ATRX gene mutations are a common feature of ALT. Specifically 19/22 ALT+ cell lines had an issue with the expression of ATRX or DAXX (Lovejoy 2012). See the Lovejoy 2012 supplementary information for the Excel table of Exon deletions in ALT cell lines. 
![ATRX_Prevents_Fork_Collapse](/Assets/ATRX_Prevents_Fork_Collapse.jpg "ATRX_Prevents_Fork_Collapse")

(Clynes 2013)

<a name="Getting_ATRX_DNA"></a>
###### Getting ATRX DNA
Searching Ensembl for human ATRX yielded ATRX-201 and ATRX-202. I picked ATRX-201 cause it has 35 exons (which matches the Lovejoy 2012 paper). It was Ensembly ENST00000373344.10. Ensembl refseq switch to NCBI Reference Sequence yielded NM_000489.5 for the gene. I saved it as NM_000489.5_homo_sapiens_ATRX_Gene.fasta.

<a name="Removing_ATRX_Exons_2_29"></a>
###### Removing ATRX Exons 2-29 
See the Lovejoy 2012 supplementary Excel table for a list of commonly missing ATRX Exons. I decided to play with the U2OS variant because that is a cell line that I used to grow :) U2OS is missing ATRX exons 2-29. NCBI says exon 2 is [236:348] and exon 29 is 6542..6719 https://www.ncbi.nlm.nih.gov/nuccore/NM_000489. I used R to remove those exons.

```r
library(seqinr)
WT_hATRX_Gene <- read.fasta("NM_000489.5_homo_sapiens_ATRX_Gene.fasta")
WT_hATRX_Gene_Nucleotides <- WT_hATRX_Gene[[1]]
length(WT_hATRX_Gene_Nucleotides)
typeof(WT_hATRX_Gene_Nucleotides)
WT_hATRX_Gene_Nucleotides
U2OS_hATRX_Gene_Nucleotide_FIRST <- WT_hATRX_Gene_Nucleotides[1:235]
U2OS_hATRX_Gene_Nucleotide_SECOND <- WT_hATRX_Gene_Nucleotides[6720:length(WT_hATRX_Gene_Nucleotides)]
U2OS_ATRX_Characters <- c(U2OS_hATRX_Gene_Nucleotide_FIRST, U2OS_hATRX_Gene_Nucleotide_SECOND)
U2OS_ATRX_DNAstring <- DNAString(paste(toupper(U2OS_ATRX_Characters), collapse = ""))
```

<a name="Sequence_Alignment_of_WT_ATRX_to_Mutant_ATRX"></a>
###### Sequence Alignment of WT ATRX to Mutant ATRX
The R msa package can't handle the full length of the ATRX gene, so I shortened it down to 400 nucleotides.
```r
# limit it to 400 ... that's more than enough to see exon absence
U2OS_ATRX_DNA_Short <- U2OS_ATRX_DNAstring[1:400]
WT_hATRX_DNA_Short <- toupper(WT_hATRX_Gene_Nucleotides[1:400])
write.fasta(sequences = U2OS_ATRX_DNA_Short, names = "U2OS_ATRX_DNA_Short", file.out = "U2OS_ATRX_DNA_Short.fasta", open = "w", nbchar = 70, as.string = FALSE)
write.fasta(sequences = WT_hATRX_DNA_Short, names = "WT_hATRX_DNA_Short", file.out = "WT_hATRX_DNA_Short.fasta", open = "w", nbchar = 70, as.string = FALSE)
library(msa)
# both_ATRX_Sequences <- read.fasta("WT_and_U2OS_hATRX.fasta")
both_ATRX_Sequences_SHORT <- "both_ATRX_Sequences_SHORT.fasta"
# typeof(both_ATRX_Sequences)
#both_ATRX_DNAStringSet <- readDNAStringSet(both_ATRX_Sequences)
#both_ATRX_Sequences_Alignment <- msa(both_ATRX_DNAStringSet)
both_ATRX_Sequences_SHORT_StringSet <- readDNAStringSet(both_ATRX_Sequences_SHORT)
both_ATRX_Sequences_Alignment_SHORT <- msa(both_ATRX_Sequences_SHORT_StringSet)
both_ATRX_Sequences_Alignment_SHORT
msaPrettyPrint(both_ATRX_Sequences_Alignment_SHORT, output="pdf", showNames="none",
showLogo="none", askForOverwrite=FALSE, verbose=TRUE)
#texi2pdf("both_ATRX_Sequences_Alignment.tex", clean=TRUE)
```
You can see that the sequences are the same until postion 236. That is where the Exon deletion for U2OS starts! 

![ATRX_Exon_Deletion_Alignment](/Assets/ATRX_Exon_Deletion_Alignment.jpg "ATRX_Exon_Deletion_Alignment")

<a name="Variants_Repeats_are_Found_in_ALT_Telomeres"></a>
#### Variants Repeats are Found in ALT Telomeres
POT1 doesn't appear to play a major role in ALT telomeres. Here's a paper that showed relatively unchanged POT1 protein levels in a pre vs. post-ALT cancer (Kamranvar 2013). What's much more interested is the distribution of variant telomeric repeats found in ALT telomeres (Conomos 2012). Telomerase cells appear to have mostly TTAGGG repeats in their telomeres, but ALT telomeres also seem to have TCAGGG repeats. There is a very interesting model of ALT that invovles these TCAGGG repeats getting bound by nuclear receptors (Conomos 2012).

Here are common telomeric sequences found in TEL+:

```r
# Conomos 2012 Figure S1 C HeLa
# Pie Chart with Percentages
slices <- c(889, 74, (0 + 8 + 94 + 8 + 6 + 7 + 4 + 2 + 471)) 
lbls <- c("TTAGGG", "TCAGGG", "Other")
pct <- round(slices/sum(slices)*100)
lbls <- paste(lbls, pct) # add percents to labels 
lbls <- paste(lbls,"%",sep="") # ad % to labels 
pie(slices,labels = lbls, col=rainbow(length(lbls)),
   main="HeLa Average Number of Telomeric Repeats")
```

![HeLa_Variant_Repeats](/Assets/HeLa_Variant_Repeats.jpg "HeLa_Variant_Repeats")

Here are common telomeric sequences found in ALT+:

```r
# Conomos 2012 Figure S1 C 
# Pie Chart with Percentages
slices <- c(10165, 4466, (528 + 332 + 241 + 108 + 76 + 73 + 63 + 31 + 3231)) 
lbls <- c("TTAGGG", "TCAGGG", "Other")
pct <- round(slices/sum(slices)*100)
lbls <- paste(lbls, pct) # add percents to labels 
lbls <- paste(lbls,"%",sep="") # ad % to labels 
pie(slices,labels = lbls, col=rainbow(length(lbls)),
   main="WI38-VA13/2RA Average Number of Telomeric Repeats")
```
![WI38_VA13_2RA_Variant_Repeat](/Assets/WI38_VA13_2RA_Variant_Repeat.jpg "WI38_VA13_2RA_Variant_Repeat")

This is the nuclear receptor recruitment model first presented in Conomos 2012:

![Conomos_2012_Variant_Repeat_ALT_Model](/Assets/Conomos_2012_Variant_Repeat_ALT_Model.jpg "Conomos_2012_Variant_Repeat_ALT_Model")

<a name="TERT_Promoter_Compaction_is_Found_in_ALT"></a>
##### TERT Promoter Compaction is Found in ALT
ALT cells commonly have long, heterogenous telomere lengths (Kumakura 2005). Mouse embryonic stem cells deficient for DNMT have HUGE telomeres. Under normal conditions, mouse subtelomeres are heavily methylated, BUT that is not the case in mESC deficient for DNMT. The lack of DNMT increased the rate of telomeric sister chromatid exchanges (T-SCE), and ALT-associated Promyelocytic Nuclear Bodies (APBs). T-SCE and APBs are both common features of ALT activity. The authors concluded that the increased telomeric recombination MIGHT lead to telomere length changes, BUT they do not exclude the involvement of telomerase in the weirdly long telomeres that were seen (Gonzalo 2006). Luckily, I found these two other papers that go into more detail about TERT chromatin compaction in ALT!

Atkinson 2005 found that chromatin modifications of hTR and hTERT promoters were commonly found in ALT activity. Treatment of ALT+ cells with 5-AZC or Trichostatin A lead to chromatin remodeling of hTR and hTERT. This induced telomerase expression. Interestingly enough they found that mehtylated Lys20 Histon H4 was not associated with gene expression, BUT does seem to be ALT specific (Atkinson 2005). This might be a new marker of ALT activity! Acetylation of H3K9 and methylation of H3K4 is known to be associated with an open chromatin conformation. In Kumakura 2005, the authors found that ALT+ cells had H3K9 methylation and low levels of H3K4 methylation and H3K9+H3K14 acetylations. The ratio of H3K9 methylation / H3K4 methylation was different across ALT+ and TEL+ cell lines. They found that treating ALT+ cells with TSC or 5-AZC caused a reversion from complete to partial methylation of the CpG islands on the hTERT promoter. They switched an E6CL TEL+ line to TEL- and it was able to grow for well over 240 population doublings (Kumakura 2005). That's some ALT activity right there!
![H3K9_H3K4_Methylation_Ratio](/Assets/H3K9_H3K4_Methylation_Ratio.jpg "H3K9_H3K4_Methylation_Ratio")

(Kumakura 2005)

<a name="Getting_The_hTERT_Sequence"></a>
###### Getting The hTERT Sequence
The UniProt entry O14746 is for hTERT https://www.uniprot.org/uniprot/O14746. Following GeneID 7015 gets TERT telomerase reverse transcriptase for humans https://www.ncbi.nlm.nih.gov/gene/7015. Note that the reverse arrow on TERT indicates that the sequence is on the reverse strand (this will become important later). I downloaded the FASTA as "NC_000005.10_hChrom5_TERT_CpG_Start.fasta". A quick text search shows that the start codon is at position 59. Take care with this sequence cause it's the reverse complement of the actual sequence!

![hTERT_NCBI_Reverse_Strand](/Assets/hTERT_NCBI_Reverse_Strand.jpg "hTERT_NCBI_Reverse_Strand")

<a name="Obtaining_hTERT_WITH_the_CpG_Island_Region"></a>
###### Obtaining hTERT WITH the CpG Island Region
Stay with me ... we're about to dig a bit into the literature! The hTERT sequence that I grabbed from NCBI DOES NOT contain the CpG island for hTERT. It doesn't even contain the normal promoter region for hTERT! Cong 1999 reports that the core hTERT promoter region is from -330 to +361 bp of the ATG start codon. HOWEVER, Kumakura 2005 found the hTERT CpG island to be from 654 bp upstream to 510 bp downstream of the ATG start codon, so this is the actual region that I need to grab! 

Grabbing the hTERT FASTA sequence from https://www.ncbi.nlm.nih.gov/gene/7015 INITIALLY is from: 1253167 to: 1295047. Checking Cong 1999 and The FASTA file, I can see that the hTERT start codon, AND a bit more of that region, of "ATGCCGCGCGCT" is at the end of the first FASTA line, which is 59 in from the left (59 is A of ATG). CpG is 654 bp upstream of the transcriptoin start site, SO going 595 back from current start site 1253167-595 = 1252572. 1252572 should be the start of the CpG island, RIGHT?!? WRONG!!! ... Why aren't I getting any more nucleotides before the current start read?!?!? OH!!! I'm looking at the reverse complement, lol! ;) 

It should be  1295047 + 595 = 1295642 YESSSSSSS, that's right :) Now I have more at the beginniig, so "atgccgcgcgctccccgct" is fully searchable! This is the new range:
https://www.ncbi.nlm.nih.gov/nuccore/NC_000005.10?report=fasta&from=1253167&to=1295642&strand=true. I saved the FASTA as NC_000005.10_hChrom5_TERT_CpG_Start.fasta. 

<a name="Analyzing_the_Alleged_CpG_Promoter_Region"></a>
###### Analyzing the Alleged CpG Promoter Region
Dessain 2000 reported that the hTERT CpG island has a GC content of 74% and a CG:GC ratio of 0.87. Is that what I get for the same region?!? I wrote code in R to get the GC content and CG:GC ratio of the hTERT CpG promoter region that I identified. I didn't comment my code ... I am sorry. Note that I picked i=1164 cause Kumakura 2005 says that the hTERT CpG island to be from 654 bp upstream to 510 bp downstream of the ATG start codon, which is 654 + 510 = 1164 :) Here's R code that I didn't bother commenting :( 

```r
dna_file <- read.fasta("/media/david/Linux/Introns_Exons_and_Promoters/hTERT_CpG_Island/NC_000005.10_hChrom5_TERT_CpG_Start.fasta")
individual_characters <- dna_file[[1]]
i <- 1
CG_count <- 0
GC_count <- 0
g_count <- 0
c_count <- 0
for (letter in individual_characters) {
  #print(letter)
  i <- i + 1
  if (letter == "g") {
    g_count <- g_count + 1
  }
  if (letter == "c") {
    c_count <- c_count + 1
  }
  if ((letter == "c") & (last_letter == "g")) {
    GC_count <- GC_count + 1
  }
  if ((letter == "g") & (last_letter == "c")) {
    CG_count <- CG_count + 1
  }
  last_letter <- letter
  if (i >= 1164) {
    break
  }
}
print(100*(c_count+g_count)/1164)
print(GC_count)
print(CG_count)
print(CG_count/GC_count)
```
The lazily unlabeled output is:

[1] 76.03093
[1] 167
[1] 141
[1] 0.8443114

Cool-ness! My GC content is 76 % and the ratio of CpG/GpC is 0.84. Recall that Dessain 2000 reported that the hTERT CpG island has a GC content of 74% and a CG:GC ratio of 0.87. I'm 2 % off of the GC content and 0.03 off of the CpG/GpC. THAT'S PRETTY GOOD FOR REPLICATING DATA FROM A PAPER THAT IS ALMOST TWO DECADES OLD :D But, what if that was just random luck? I re-ran that same R code on the region AFTER the CpG island and I got wildly different data. Here's that code (yes, I should've used a function; I am lazy, lol):

```r
dna_file <- read.fasta("/media/david/Linux/Introns_Exons_and_Promoters/hTERT_CpG_Island/NC_000005.10_hChrom5_TERT_CpG_Start.fasta")
individual_characters <- dna_file[[1]]
#individual_characters[5]
i <- 1164
CG_count <- 0
GC_count <- 0
g_count <- 0
c_count <- 0
for (letter in individual_characters) {
  if (i <1164) {
    next
  }
  #print(letter)
  i <- i + 1
  if (letter == "g") {
    g_count <- g_count + 1
  }
  if (letter == "c") {
    c_count <- c_count + 1
  }
  if ((letter == "c") & (last_letter == "g")) {
    GC_count <- GC_count + 1
  }
  if ((letter == "g") & (last_letter == "c")) {
    CG_count <- CG_count + 1
  }
  last_letter <- letter
  
  
  if (i >= 42476) {
    break
  }
}
print(100*(c_count+g_count)/41312)
print(GC_count)
print(CG_count)
print(CG_count/GC_count)
```

The lazily unlabeled output is:

[1] 58.55926
[1] 3047
[1] 1654
[1] 0.542829

My GC content is 58.5 % and the ratio of CpG/GpC is 0.54. Recall that Dessain 2000 reported that the hTERT CpG island has a GC content of 74% and a CG:GC ratio of 0.87. THE REGION THAT IS NOT A CpG ISLAND IS 15.5% off of the GC content and 0.33 off of the CpG/GpC. I could dig into this with more statistical rigor, but I think you get the idea. I'M EXCITED!!! This was a really cool biological programming exercise!!! :D

<a name="STN1_Mutation_Triggers_ALT_in_Yeast"></a>
#### STN1 Mutation Triggers ALT in Yeast
ADDED STUFF
Counter 1996 The roles of telomeres and telomerase in cell life span
Yeast also can undergo a cellular catastrophe
analogous to the crisis induced in transformed human cells by the loss of telomeric DNA. Disruption
of any one of the S. ceret'isiae genes EST1, KEMI,
or TCL1 (TER1 in K. lactus) results in a loss of
telomeric DNA at the rate of approximately ~ 3-5
bp/generation. This shortening is accompanied by a
gradual increase in cell and chromosome loss. By
approximately generation 100, most cells perish
[7,57,58,162].
Counter 1996 The roles of telomeres and telomerase in cell life span
ADDED STUFF


ALT is a recombination-based telomere maintenace mechanism used by some human cancers to maintain cellular immortality. ALT cells typically have widly long, heterogenous telomeres. The exact molecular mechanism involved in this pathway are unknown. Iyer 2005 found that a STN1 gene mutation can initiate ALT in the yeast Kluyveromyces lactis. These ALT-like yeast cells experience a rapid telomere shortening when WT STN1 is re-introduced (Iyer 2005). There aren't any neat figures in this paper to talk about, so I'm going to try to replicate the protein multiple sequence alignment from Iyer 2005 figure 4. STN1 is aligned from K. lactis S. cerevisiae (Sc) and Candida glabrata (Cgl).

![Yeast_Protein_Alignment](/Assets/Yeast_Protein_Alignment.jpg "Yeast_Protein_Alignment")

<a name="Obtaining_STN1_From_3_Yeast_Organisms"></a>
###### Obtaining STN1 From 3 Yeast Organisms
The paper states that the S. cerevisiae (Sc) and Candida glabrata (Cgl) GenBank accession numbers are P_38960 and XP_448655. HOWEVER, it wasn't that easy to find the sequences cause those accession numbers are from back in 2005. NCBI says "The following term was not found in Nucleotide: P_38960." The XP_448655 is here: https://www.ncbi.nlm.nih.gov/protein/XP_448655. I had trouble finding the sequence for K. lactis they were talking about. Here's the crazy search term that I used on NCBI:

and it's the only result (other than whole chromosome chunks) w/ this crazy search term I made:
(((stn1) NOT "Pyrenophora tritici-repentis"[porgn:__txid45151] NOT "Fusarium fujikuroi"[porgn:__txid5127] NOT "[Candida] glabrata"[porgn:__txid5478] NOT "Hortaea werneckii"[porgn:__txid91943] NOT "Saccharomyces cerevisiae"[porgn:__txid4932]) NOT "Metarhizium robertsii"[porgn:__txid568076] NOT "Fusarium sp. FIESC_5 CS3069"[porgn:__txid1318460] NOT "Fusarium pseudograminearum CS3487"[porgn:__txid1318458] NOT "Fusarium pseudograminearum CS3427"[porgn:__txid1318457] NOT "Fusarium pseudograminearum CS3220"[porgn:__txid1318456] NOT "Fonsecaea multimorphosa"[porgn:__txid979981] NOT "Cladophialophora immunda"[porgn:__txid569365] NOT "Aspergillus nidulans FGSC A4"[porgn:__txid227321] NOT "Candida viswanathii"[porgn:__txid5486] NOT "Zygosaccharomyces bailii"[porgn:__txid4954] NOT "Metarhizium anisopliae"[porgn:__txid5530] NOT "Aspergillus flavus"[porgn:__txid5059] NOT "Talaromyces atroroseus"[porgn:__txid1441469] NOT "[Candida] auris"[porgn:__txid498019] NOT "Zygosaccharomyces rouxii"[porgn:__txid4956] NOT "[Candida] boidinii"[porgn:__txid5477] NOT "Komagataella phaffii"[porgn:__txid460519] NOT "Aspergillus fumigatus"[porgn:__txid746128] NOT "Candida albicans SC5314"[porgn:__txid237561] NOT "Yarrowia lipolytica"[porgn:__txid4952]) AND "Kluyveromyces lactis"[porgn:__txid28985] 

... I'm pretty sure that it's NCBI Reference Sequence: XM_452728.1, titled "Kluyveromyces lactis uncharacterized protein (KLLA0_C11825g), partial mRNA" BECAUSE that entry has this note "cerevisiae YDR082W STN1 Protein involved in telomere length regulation functions in telomere metabolism during late S phase." S. ceriviasa yeast was easier to find cause it's got stn1p in the title :) https://www.ncbi.nlm.nih.gov/nuccore/NM_001180390.1

<a name="Attempt_to_Replicate_Lyer_2005_Figure_4"></a>                     
###### Attempt to Replicate Lyer 2005 Figure 4
I used the R msa library to align the three yeast organism STN1 proteins that were obtained above. I'm not too happy with this alignment :( The authors state that "The protein
sequences were aligned in ClustalW using default values." HOWEVER, the R msa package that I used was set to use ClustalW default values and it didn't replicate Figure 4 from Lyer 2005. The protein sequences seem to match (at least by eye). I'm not really sure where I went wrong here. I've only played with sequence alignment a little bit, so I'm probably doing something wrong. Anyway, here's the code:

```r
setwd("/media/david/Linux/Introns_Exons_and_Promoters/Yeast_STN1_ALT/Proteins")

library(msa)
All_Yeast_STN1_Protein <- "All_Yeast_STN1_Protein.fasta"
All_Yeast_STN1_Protein <- readDNAStringSet(All_Yeast_STN1_Protein)
All_Yeast_STN1_Protein_alignment <- msa(All_Yeast_STN1_Protein)
All_Yeast_STN1_Protein_alignment
msaPrettyPrint(All_Yeast_STN1_Protein_alignment, output="pdf", showNames="none",
showLogo="none", askForOverwrite=FALSE, verbose=FALSE)
```

![Aligning_Yeast_STN1_Proteins](/Assets/Aligning_Yeast_STN1_Proteins.jpg "Aligning_Yeast_STN1_Proteins")

<a name="Aligning_Human_Yeast_and_Frog_STN1"></a>
###### Aligning Human, Yeast, and Frog STN1
Cohen 2002 reported that Xenopus laevis form extrachromosomal circular telomeric DNA. This is commonly associated with ALT! I briefly looked around for reptile ALT and this is the closest thing I could find. I'm not convinced that the activity reported by Cohen 2002 was actually ALT. This alignment isn't really related to anything. I just made it mostly for fun ... well, it's kinda connected to ALT and I know a herpetologist that might enjoy seeing frogs getting included in this repo ;) 

Cohen 2002 Formation of extrachromosomal circles from telomeric DNA in Xenopus laevis 
```r
Klactis_Xenopus_Human_STN1_Proteins <- "Klactis_Xenopus_Human_STN1_Proteins.fasta"
Klactis_Xenopus_Human_STN1_Proteins_AA <- readAAStringSet(Klactis_Xenopus_Human_STN1_Proteins)
Klactis_Xenopus_Human_STN1_Proteins_AA_alignment <- msa(Klactis_Xenopus_Human_STN1_Proteins_AA)
Klactis_Xenopus_Human_STN1_Proteins_AA_alignment
msaPrettyPrint(Klactis_Xenopus_Human_STN1_Proteins_AA_alignment, output="pdf", showNames="none",
showLogo="none", askForOverwrite=FALSE, verbose=FALSE)
```
![Klactis_Xenopus_Human_STN1_Proteins_AA_alignment](/Assets/Klactis_Xenopus_Human_STN1_Proteins_AA_alignment.jpg "Klactis_Xenopus_Human_STN1_Proteins_AA_alignment")

<a name="Ever_Shorter_Telomeres"></a>
# Ever Shorter Telomeres
EST has two cases: mild telomerase activity and extrememly long initial telomere lengths.

<a name="Mild_Telomerase_Activity"></a>
#### Mild Telomerase Acitivty Can Keep Cancers Dividing Long Enough for Metastasis

```r
# Viceconte 2017 ~10 kb at p12 down to ~5kb LB2901-MEL (hTERT neg ), LB3129-MELA, and LB3129-MELB (hTR neg )
# Viceconte 2017 down to ~6 and 3kb LB2870-MEL and LB2687-MEL TRAP pos melanoma, shortening in culture ... did not go through crisis?
# how many population doublings?
# LB2870-MEL/TEL + (p21), LB2687-MEL/TEL + (p25), and in LB2901-MEL (p16) and LB3129-MELB (p21)
# 3129 mela p22 crisis, 3129 melb p26 crisis, lb2901 mel p25 crisis
viceconte_telomere_lengths <- list()
viceconte_number_cells <- list()
no_telomerase_lengths <- list()
EST_telomerase_start_length <- 4000
no_telomerase_start_length <- 4000
current_length <- EST_telomerase_start_length
current_no_telomerase_length <- no_telomerase_start_length
current_no_telomerase_division_number <- 0
dividing <- TRUE
division_number <- 0
cell_number <- 1
no_telomerase_number_cells <- 1
while(dividing) {
  viceconte_telomere_lengths[division_number] <- current_length
  viceconte_number_cells[division_number] <- cell_number
  
  # telomere shortening
  while(current_no_telomerase_length > 3000){
    no_telomerase_lengths[current_no_telomerase_division_number] <- current_no_telomerase_length
    current_no_telomerase_length <- current_no_telomerase_length -50
    no_telomerase_number_cells <- no_telomerase_number_cells * 2
    current_no_telomerase_division_number <- current_no_telomerase_division_number + 1
  }
  
  current_length <- current_length - 50
  # low-level telomerase
  current_length <- current_length + 25
  if(current_length < 3000) {
    dividing <- FALSE
  }
  division_number <- division_number + 1
  cell_number <- cell_number * 2
  
}
print(division_number)
print(cell_number)
plot(as.numeric(viceconte_telomere_lengths), col="red", type="l", pch=19, lty=2, xlab="Division Number", ylab="Telomere Length (bp)", main="Telomere Shortening is Slowed with Ever Shorter Telomeres Activity")
lines(as.numeric(no_telomerase_lengths), col="green", type="l", pch=19, lty=2)
legend(20, 3800, legend=c("Ever Shorter Telomeres", "Normal Telomere Shortening"), col=c("red", "green"), lty=2:2, cex=0.8)
#plot(as.numeric(no_telomerase_lengths))
#plot(as.numeric(viceconte_number_cells))
# plot(as.numeric(no_telomerase_number_cells))
```

![ever_short_telomerase_activity](/Assets/ever_short_telomerase_activity.jpg "ever_short_telomerase_activity")

<a name="Long_Initial_Telomere_Lengths"></a>
#### Long Initial Telomere Lengths Can Keep Cancers Dividing Long Enough for Metastasis

```r
# Dagg 2017 telomeres progressively shortening over 200 pd EST. single cell 40 cell divisions is 2^40 cells ~ 1 kg
# assuming all cells survive, enough nutrients etc., prob need multiple rounds clonal evolution for enough mutations
# telomerase during embryogenesis? no telomere trimming? NO t-cicrles in EST lines. unopposed telomerase during embryogenesis, excesisve tel lengthening 
# COG-N-291 and LA-N-6 TRF mean 31.0 and 37.8 kb, highly heterogenous telomere lengths
EST_long_start_length <- 15000
current_length <- EST_long_start_length
dividing <- TRUE
division_number <- 0
cell_number <- 1
cell_number_list <- list()
while(dividing) {
  # telomere shortening
  current_length <- current_length - 50
  if(current_length < 3000) {
    dividing <- FALSE
  }
  division_number <- division_number + 1
  cell_number <- cell_number * 2
  cell_number_list[division_number] <- cell_number
}
print(division_number)
print(cell_number)
plot(as.numeric(cell_number_list), xlim=c(1, 21), ylim=c(0, 1250000), col="red", type="p", pch=19, lty=2, xlab="Division Number", ylab="Cell Number", main="Ever Shorter Telomere Cells Can Divide Extensively")
```

![ever_shorter_long_telomeres](/Assets/ever_shorter_long_telomeres.jpg "ever_shorter_long_telomeres")

<a name="Conclusion"></a>
# Conclusion
Inhibiting telomere maintenance mechanisms does initially seem like a universal approach to fighting cancer, but it does have faults. Telomerase inhibition does seem to fight cancer, but I have shown cases where it causes Hematopoietic Stem Cell problems. Preliminary evidence suggests that turning off the alternative lengthening of telomeres mechanism may slow down the DNA Damage Response and, it is possible, that stem cells require intermittent ALT activity. Evern if you ignore the issues with a dual inhibition approach to telomerase and ALT, there is still the problem of the Ever Shorter Telomeres phenotype. The mild telomerase activity found in certain EST cells may be stopped by anti-telomerase approaches. However, the long telomere EST cells with a dysfunctional telomere trimming mechanism will need an additional approach. The dual telomere maintenance mechanism approach may need to include a method of specifically trimming telomere lengths in cancer cells without shortening stem cell telomeres. It's an extradinarily complicated challenge, but certainly one that should receive continued research support. Other anti-cancer approaches like immunotherapy may be a better therapeutic approach.



<a name="Citations"></a>
# Citations
NOTE: I AM WAYYYYYY BEHIND ON UPDATING THE CITATIONS LIST ... SORRY! Please message me if you have any questions about the papers that I mentioned throughout this review :)
* Cheng 2012 Caenorhabditis elegans POT-2 telomere protein represses a mode of alternative lengthening of telomeres with normal telomere lengths
* Cong 1999 The human telomerase catalytic subunit hTERT: organization of the gene and characterization of the promoter
* Lovejoy 2012 PLoS Genet Loss of ATRX, genome instability, altered DNA damage response hallmarks of ALT pathway
* Clynes 2013 Curr Opin Genet Dev ATRX and the replication of structured DNA
* Gonzalo 2006 DNA methyltransferases control telomere length and telomere recombination in mammalian cells.pdf
* Atkinson 2005 Lack of Telomerase Gene Expression in Alternative Lengthening of Telomere Cells Is Associated with Chromatin Remodeling of the hTR and hTERT Gene Promoters
* Kumakura 2005 Reversible Conversion of Immortal Human Cells from Telomerase-Positive to Telomerase-Negative Cells
* Cong 1999 The human telomerase catalytic subunit hTERT: organization of the gene and characterization of the promoter
* Dessain 2000 Methylation of the Human Telomerase Gene CpG Island
* Cheng 2012 Caenorhabditis elegans POT-2 telomere protein represses a mode of alternative lengthening of telomeres with normal telomere lengths
* Boeck 2016 The time resolved transcriptome of C. elegans
* Iyer 2005 A Mutation in the STN1 Gene Triggers an Alternative Lengthening of Telomere-Like Runaway Recombinational Telomere Elongation and Rapid Deletion in Yeast
* Cohen 2002 Formation of extrachromosomal circles from telomeric DNA in Xenopus laevis 
* Hu 2017 Imetelstat, a Telomerase Inhibitor, Is Capable of Depleting Myelofibrosis Hematopoietic Stem Cells and Progenitor Cells
* Weissman 2001 Telomere Shortening Accompanies Increased Cell Cycle Activity during Serial Transplantation of Hematopoietic Stem Cells
* Cesare 2010 Alternative lengthening of telomeres: models, mechanisms and implications
* Shay 2012 Cancer and Telomeres −− An ALTernative to Telomerase
* Harley 2008 Telomerase and cancer therapeutics
* Sahin 2012 Antitelomerase therapy provokes ALT and mitochondrial adaptive mechanisms in cancer
* Gocha 2013 Human Sarcomas Are Mosaic for Telomerase-Dependent and Telomerase-Independent Telomere Maintenance Mechanisms
* Kalmbach 2014 Telomere Length Reprogramming in Embryos and Stem Cells
* Huang 2014 Telomere regulation in pluripotent stem cells
* Dagg 2017 Extensive Proliferation of Human Cancer Cells with Ever-Shorter Telomeres
* Suda 2002 Interchromosomal Telomere Length Variation
* Cristofari 2006 Telomere length homeostasis requires that telomerase levels are limiting
* Gavory 2002 Minimum length requirement of the alignment domain of human telomerase RNA to sustain catalytic activity in vitro
* Murnane 1994 Telomere dynamics in an immortal human cell line
* Telomere elongation in immortal human cells without detectable telomerase activity
* Kamranvar 2013 Telomere dysfunction and activation of alternative lengthening of telomeres in B-lymphocytes infected by Epstein-Barr virus
* Hastie 1990 Telomere reduction in human colorectal carcinoma and with aging
* Blackburn 2001 Switching and signaling at the telomere
