# A fluorescence based neutralization assay for influenza virus

## Overview

The basic idea behind these assays is to use reverse-genetics to generate conditionally replicative influenza viruses with GFP packaged in place of PB1.
These viruses are grown on cells constitutively expressing PB1 protein (they can undergo multi-cycle replication in those cells, but not other cells).

These PB1flank-GFP viruses are then incubated with dilutions of antibody and used to infect the PB1-expressing cells in a 96-well plate.
If this is done in the correct media (media with low autofluorescence at the GFP wavelength), then you can simply read out the fluorescence on a 96-well plate reader.
You can then use these fluorescence readings to fit a neutralization curve (if you are a Python user, you can even fit these using the [appropriate function in dms_tools2](https://jbloomlab.github.io/dms_tools2/dms_tools2.neutcurve.html)).

To understand the assays in more detail, read the protocol in Katie Hooper's original paper that developed these assays ([Hooper et al (2013)](https://jvi.asm.org/content/87/23/12531.full)) and the more detailed protocol in one of Mike Doud's papers ([Doud et al (2017)](https://journals.plos.org/plospathogens/article?id=10.1371/journal.ppat.1006271)).
Juhye Lee has also generously written up her protocol and some example lab notes:
  - [Juhye's protocol](protocols/JuhyeLeeProtocol.pdf).
  - [Juhye's lab notes](protocols/NeutralizationAssayNotebook.pdf)

In addition, if you are working with any virus other than WSN (which is trypsin independent), we now recommend using TMPRSS2-expressing cells to activate HA.
This is both easier and works better than adding exogenous trypsin.
See Juhye Lee's paper ([Lee et al (2018)](http://www.pnas.org/content/115/35/E8276)) for details.
Note that we only have MDCK-SIAT1 cells expressing TMPRSS2, so during initial reverse genetics you also have to transfect in the TMPRSS2 plasmid so that the 293T cells express it too.

## Key points
Here are some key points in the protocols to pay attention to:

 - The media is important. Most media has high GFP autofluorescence which is due to lots of riboflavin. Our neutralization assay media doesn't have this. So you need to perform your assays in this media, and also produce (or **heavily** dilute) your virus into it. You can purchase the Medium 199 we use in our neutralization assay media [here](https://www.thermofisher.com/order/catalog/product/11043023).

 - When growing PB1flank-GFP viruses, the virus becomes somewhat more sensitive to the growth stage of the cells than "full" influenza viruses, probably because it relies on the cells to produce the PB1 protein. In particular, it doesn't grow well in fully confluent cells probably because they reduce expression of PB1. So make sure that you are growing the virus in subconfluent cells, which can sometimes be hard because these cells grow so fast.

 - You can titer the virus by flow cytometry on fixed infected cells, or simply make serial dilutions in a 96-well plate, and read on the plate reader as for the neutralization assays to find a concentration that is near the top of the linear range. This is important--you need to be in the range where the signal goes down as you use less virus. When the assay works well on our plate reader, the "background" signal in wells that receive virus / media but no cells might be about 5,000 units, whereas the maximal signal in the fully infected cells might be 50,000 -- so if your plate reader is similar, that provides some indication of the expected signal to noise. If the background is much higher relative to the signal, then your media is probably somehow having a lot of autofluorescence.

## What to request from the Bloom lab
If you want to run this assay, you will typically need to request the following reagents:

 - The *pHH-PB1flank-eGFP* plasmid (see *Plasmids* section below). This is what you will use in the place of the standard PB1 reverse genetics plasmid.

 - The *293T-CMV-PB1* cells. These are the 293T cells you will use during reverse genetics, since they provide complementing PB1 protein for the PB1-deficient virus.

 - The *MDCK-SIAT1-PB1* cells and/or the *MDCK-SIAT1-PB1-TMPRSS2* cells. These are the MDCK cells that you will use during reverse genetics, since they provide complementing PB1 protein for the PB1-deficient virus. If you are using the WSN virus (which is trypsin independent) then you can use the *MDCK-SIAT1-PB1* cells. If you are using any other virus, we recommend the *MDCK-SIAT1-PB1-TMPRSS2* cells as the TMPRSS2 obviates the need to add trypsin (and works better than trypsin in our hands anyway).

 - The *pHAGE2-EF1aInt-TMPRSS2-IRES-mCherry* plasmid. If you are using TMPRSS2 in place of trypsin, transform this into the co-culture during reverse genetics so that the 293T-CMV-PB1 cells are expressing TMPRSS2 as well.

 - The other reverse genetics plasmids. You will need standard reverse genetics plasmids for the other seven (non-PB1) genes. We usually use the WSN genes (pHW181-PB2, pHW183-PA, pHW185-NP, pHW187-M, and pHW188-NS as described by [Hoffmann et al (2000)](http://www.pnas.org/content/97/11/6108)) for the six internal genes. You also need plasmids encoding your HA and NA of interest. If you just care about HA, we typically use the WSN NA. Unfortunately these WSN reverse genetics plasmids are covered by one of the many onerous MTAs that plague the flu field. So if you want us to send you those, you have to first complete an MTA to get St. Judes to grant you permission to receive them from us. If you dig through our papers, you'll also find that we have cloned various other HAs that we might be able to send you. Alternatively, you may already have the HA of interest cloned into a plasmid yourself.

## Citations
We (specifically Katie Hooper, Mike Doud, Juhye Lee, and Jesse Bloom) put a fair amount of work into developing this assay. 
So if you use it, we'd appreciate if you cite the relevant papers describing the reagents:

 - The system that Jesse developed to grow viruses with GFP in the PB1 segment is described in [Bloom et al (2010)](http://science.sciencemag.org/content/328/5983/1272.long).

 - Katie's development of an appropriate medium and assay to simply read out the assays by GFP is described in [Hooper et al (2013)](https://jvi.asm.org/content/87/23/12531.full). If you feel that you can only afford to cite one paper, this is probably the best one.

 - Mike's paper that further optimized the assay and that gives a really detailed protocol is [Doud et al (2017)](https://journals.plos.org/plospathogens/article?id=10.1371/journal.ppat.1006271).

 - If you use the TMPRSS2-expressing cells to obviate the need for trypsin, then please cite Juhye's paper describing these cells. This is [Lee et al (2018)](http://www.pnas.org/content/115/35/E8276).

## Plasmids
The maps of plasmids relevant to this neutralization assay are in the [./plasmid_maps](plasmid_maps) subdirectory.
The maps are in Genbank format.
Specifically, they are:

 - [208_pHH_PB1flank_eGFP](plasmid_maps/208_pHH_PB1flank_eGFP.gb): Encodes GFP in the PB1 gene segment in the context of a human PolI promoter. The reference for this plasmid is [Bloom et al (2010)](http://science.sciencemag.org/content/328/5983/1272.long).

 - [195_pHAGE2_CMV_PB1_W](plasmid_maps/195_pHAGE2_CMV_PB1_W.gb): Lentiviral plasmid used to transduce 293T and MDCK-SIAT1 cells to make 293T-CMV-PB1 and MDCK-SIAT1-CMV-PB1 cells. The reference for this plasmid is [Bloom et al (2010)](http://science.sciencemag.org/content/328/5983/1272.long).

 - [1422_pHAGE2_EF1aInt_TMPRSS2_IRES_mCherry](plasmid_maps/1422_pHAGE2_EF1aInt_TMPRSS2_IRES_mCherry.gb): Lentiviral plasmid expressing the TMPRSS2 protease. The reference for this plasmid is [Lee et al (2018)](http://www.pnas.org/content/115/35/E8276).


