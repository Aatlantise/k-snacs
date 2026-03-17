# K-SNACS Dataset and Guidelines
**Korean Semantic Network of Adposition and Case Supersense**

## Dataset

**File:** [little_prince_ko.conllulex](./little_prince_ko.conllulex)

**Data Version:**  
* Current: 1.2
* Compatible with K-SNACS Guidelines v0.9

**Data Info:** 
* Title: 어린 왕자 (erin wangca) "The Little Prince"
* Author: Atoine de Saint-Exupéry 
* Original Language: French (Le Petit Prince)
* Genre: Childrens literature, Novella

**Column Description:**
Each token line has the following 19 columns, with _ indicating an empty value in a column.

The first 10 columns are copied exactly from the UD_English corpus following the UDv2 standard. TODO: The UD_English version is ..., subsequent to 2.0 to incorporate corrections (primarily to lemmas and POS tags). Refer to this page and others on the UD website for documentation of UD's conventions for encoding orthography, morphology, and syntax.

* ID: Word index: an integer starting at 1 for each new sentence, or a decimal number for empty nodes that capture ellipsis phenomena. Empty nodes are listed but ignored for purposes of lexical semantics. 
* FORM: Word form or punctuation symbol.
* LEMMA: Lemma or stem of word form.
* UPOS: Universal part-of-speech tag, e.g. ADP for adpositions.
* XPOS: Language-specific part-of-speech tag. For UD_English this comes from the Penn Treebank (PTB) tagset: e.g. IN for adpositions and subordinating conjunctions. 
* FEATS: List of morphological features, separated by | symbols.
* HEAD: Head of the current word, which is either a value of ID or zero (0).
* DEPREL: Dependency relation to the HEAD, e.g. obj for direct object (root iff HEAD = 0).
* DEPS: Enhanced dependency graph in the form of a list of head-deprel pairs.
* MISC: Any other annotation. In this corpus, for non-empty (regular) token nodes, the only thing that goes here is SpaceAfter=No to indicate how the tokenization maps to the original sentence string. 
* SMWE: Two integers, the first identifying a strong MWE grouping of tokens, and the second identifying the current token's position relative to the other tokens that form the MWE. E.g., in the above example, have and experience form a (discontinuous) strong MWE; have has 1:1 in the SMWE column and experience has 1:2. Both integers are 1-based. 
* LEXCAT: A syntactic category that applies to strong lexical expressions (strong MWEs and single-word expressions, regardless of whether they belong to a weak MWE). The set of valid supersense labels (SS and SS2) is determined based on LEXCAT. 
* Possible values of LEXCAT are: N (noun, common or proper), PRON (non-possessive pronoun, including indefinites like someone), PRON.POSS (possessive pronoun), POSS (possessive clitic), V (full verb or copula), AUX (auxiliary), P (single-word or compound adposition), PP (prepositional phrase MWE), INF (nonsemantic infinitive marker to or infinitive-subject-marker for), INF.P (infinitive maker to when it receives an adposition supersense), DISC (discourse/pragmatic expression); and ADJ, ADV, DET, CCONJ, SCONJ, INTJ, NUM, SYM, PUNCT, X, which are in line with Universal part-of-speech tags. Strong verbal multiword expressions are subtyped, thus receiving a LEXCAT of V.VID, V.VPC.full, V.VPC.semi, V.LVC.full, V.LVC.cause, or V.IAV per PARSEME Shared Task 1.1 Guidelines. 
* LEXLEMMA: The lemma(s) of the component word(s) of the strong expression (single- or multiword) that begins with the current token. _ for non-initial tokens in a strong MWE. Thus, for have, LEXLEMMA is have experience, while for experience it is _. 
* SS: Supersense label, if applicable, and the token is initial within its strong expression. Noun supersense label (prefixed with n.; requires LEXCAT=N), verb supersense label (prefixed with v.; requires LEXCAT=V), or adposition supersense label (prefixed with p.; requires LEXCAT=P, PP, INF.P, POSS, or PRON.POSS). Special values are  `$ (opaque possessive slot in idiom; requires LEXCAT=POSS or PRON.POSS) and ?? (unable to assign a supersense because the usage is unintelligible, incomplete, marginal, or nonnative). 
* SS2: Second supersense label; used only for adpositional expressions, which always have two labels listed, a role label in SS and a function label in SS2 (often these are identical). 
* WMWE: Weak MWE grouping and position, analogous to the SMWE column. In the example, have experience w forms a weak MWE, and this is indicated with WMWE=3:1, 3:2, and 3:3 on the respective tokens. Weak MWE identifiers are kept distinct from strong MWE identifiers. 
* WCAT: Placeholder for a weak MWE category (currently not used). 
* WLEMMA: If the token begins a weak MWE, as have does, then this column holds the lemmas of its constituent words. Otherwise, it is blank (_). 
* LEXTAG: BIO-style tag summarizing the full lexical analysis, including any strong and weak MWE segmentations, LEXCAT, and supersenses. This is intended for sequence taggers.
* The BIO symbols are: O for token not belonging to any MWE, B for the token beginning an MWE, I_ for a token continuing a strong MWE, and I~ for a token continuing a weak MWE. Lowercase variants o, b, i_, and i~ apply when the token is contained within a separate discontinuous MWE.

If the token is not continuing a strong expression (i.e. everything but I_ and i_), the LEXCAT and supersense (if applicable) are appended following hyphens. If SS and SS2 are identical, only one copy is included in the tag; if they differ, they are rendered as SS|SS2.

Thus, for the tokens have a good experience w, the respective LEXTAG values are:

have: B-V.LVC.full-v.stative - begins an MWE, verbal, subtype LVC.full (full light verb construction), stative supersense
a: o-DET - not part of any MWE, but contained within one; determiner, no supersense
good: o-ADJ - not part of any MWE, but contained within one; adjective, no supersense
experience: I_ - attaches to the most recent non-O/o token (have) to join it in a strong MWE
w: I~-P-p.Topic - attaches non-O/o token (experience) to join its strong expression (have experience) into a weak expression with whatever strong expression contains w. Adpositional; SS and SS2 are both p.Topic.

**License:**
This dataset's supersense annotations are licensed under CC BY 4.0 ([Creative Commons Attribution-ShareAlike 4.0 International license](https://creativecommons.org/licenses/by/4.0/legalcode)).

## K-SNACS Guidelines

**File:** [k-snacs-guideline-appendix-v0.9.pdf](k-snacs-guideline-appendix-v0.9.pdf)

**Guideline Version:**
* Current: 0.9
* Compatible with [English SNACS v2.5](https://arxiv.org/abs/1704.02134)
* Please note that this document is an appendix to the above English SNACS guidelines, including only language-specific information that merits further detailing. For full definitions of labels and use cases, please refer to [English guidelines](https://arxiv.org/abs/1704.02134).


## Paper
Please cite the following when using this data:

[Hwang et al., 2020](https://www.aclweb.org/anthology/2020.dmr-1.6/):
> Hwang, Jena D., Hanwool Choe, Na-Rae Han, and Nathan Schneider. "K-SNACS: Annotating Korean adposition semantics." In Proceedings of the Second International Workshop on Designing Meaning Representations. 2020. 



## K-SNACS Team

### Key Collaborators:

* [Jena Hwang](https://jdch00.github.io/) - Allen Institute for AI
* [Na-Rae Han](http://www.pitt.edu/~naraehan/) - University Pittsburgh 
* [Hanwool Choe](https://english.hku.hk/people/Faculty/258/Dr_Hanwool_Choe) - Hong Kong University
* [Junghyun Min](https://aatlantise.science/) - Georgetown University
* [Nathan Schneider](http://people.cs.georgetown.edu/nschneid/) - Georgetown University
* [Elli Ahn](https://rsea.fas.harvard.edu/people/elli-ahn) - Harvard University

### Special Thanks to:

* [Vivek Srikumar](https://svivek.com/) - University of Utah
* [Austin Blodgett](https://www.austinblodgett.org/) - Georgetown University


### This research was supported in part by:

* NSF award IIS-1812778
* BSF grant 2016375