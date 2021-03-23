A beginner’s exploration of Norwegian Bokmål grammar in foma

-	Introduction
As a graduate in Translation and Interpreting, I find myself quite interested in languages.
Even though I can only speak Spanish and English fluently, I have dabbled in some other languages, such as Italian, German, Norwegian and Esperanto.
However, I have always been particularly interested in Scandinavian languages, perhaps due to the difficulty reputation they have acquired (I can’t deny a challenge).

Thus, when I was proposed to write a small foma program with a language of my choosing, I was certain I would go with this language.

I would like to add that there is further explanation commented in both files, as it was easy to point out the sections I wanted to talk about.
Furthermore, be wary of possible mistakes as my Norwegian is very much in progress.

-	First steps
A grammar is all I needed to start with the program.
It was a tad more complicated than I expected; Norwegian is not the most popular language out there, but I found several pages and online books that gave me all the knowledge I needed for this small program. Refer to the bibliography for further knowledge.

-	The basics
This small program needed a few things to be stable enough: a few dozen stems (nouns and verbs) and several inflectional morphemes.
I also tried adding some derivational morphemes.
I should add that the name of the different parts in the lexc file are in Norwegian except the root. For instance, instead of prefixes, I used ‘prefiks’.

-	Contents
The lexc file contains 33 verbs, 18 nouns, auxiliary verbs for the main verbs, a preposition, a prefix and two suffixes.

-	Verbs
In Norwegian, verb conjugation for regular verbs (or, as Norwegians call them, weak verbs) is pretty straightforward: they have four conjugations.
Thus, in the ‘VerbStamme’ part of the lexc file, every verb connects to its given conjugation (‘StammeInfl1’, ‘StammeInfl12’, ‘StammeInfl3’ and ‘StammeInfl4’, meaning ‘inflection of the stem’).
Then, each tense inside the conjugations directs to the unification and/or disabling flag of the auxiliary verbs or the pronoun declared in the beginning.
For example, the present future starts with a ‘will’, in Norwegian ‘vil’, so that tense directs to the flag ‘@U.VIL.ON’, as well as the disabling flags for the rest of the beginnings (@D.HAR@, @D.HADDE@, and so on).

Irregular verbs (or, as Norwegians call them, strong verbs), however, are a bit more complicated.
Some of them have some similarity with certain tenses of some conjugations, which is why I tried to indicate the exceptions in the ‘norwegian.foma’ file and use as much of the rest conjugations as possible.
Nonetheless, the output was recognising the wrong conjugation as well as the exception I wrote down.
Thus, I created a new part in the lexc file called ‘Sterke’ (strong), where I declared only the coinciding tenses of all the irregular verbs (the infinitive and imperative) and declared the rest in the foma file.

!!! This is REALLY important -> when applying up in foma, as explained in the file, you have to add the auxiliary verb or the pronoun of the given tense (using underscores as white spaces) in order to get a result, such as ‘vil_ha_levd’ to get ‘lev+V+PretFut’. Find more information in line 68 of the foma file. !!!

Furthermore, in the foma file some rules are declared for verbs. When conjugated, some verbs lose the double consonant before the new suffix is added.

-	Nouns
For the nouns, I had previously declared the ‘bi-‘ prefix as a flag for all of the nouns, so I had to add a disabling flag to all those nouns that needn’t that prefix.
I am aware this is a very complicated way of putting this, but I was unable to make it work without the disabling flag.

Moreover, all of the nouns are conjugated according to their gender: masculine, feminine or neuter, declared almost at the end of the file. These don’t use flags.

Some of the nouns contain a unification flag for two suffixes: ‘-gjenger’ and ‘-taker’.
This flag allows these nouns to form the noun itself plus the noun with the suffix, which makes a new word.
For example, ‘kirke’ is ‘church’ and ‘kirkegjenger’ is a ‘churchgoer; someone who goes to church’. Also, these nouns are conjugated both ‘raw’ and with the suffix added.

Finally, in the foma file, there are two rules written: one, the ‘eToæTransformation’, which transforms some of the irregular nouns which have a double ‘ee’ into an æ in the plural.
The second one is ‘IrregularNounConjugation’: those masculine irregular nouns ending in ‘-er’, like ‘politiker’, ‘jeger’ or ‘kirkegjenger’, have a different conjugation for the plural, declared in this rule.


-	Room for improvement
As I have previously mentioned, due to time restriction, there are some things I would have liked to change or improve.
The list below shows the things I would like to work on further down the line. Unfortunately, for this assignment I found it impossible.
o	The appearance of the wrong conjugation(s) after having defined an exception.

o	To be able to use suffixes and prefixes for verbs that can be transformed into nouns.
For example, ‘fall’ can be a verb or a noun, but I had to declare it twice: once under the verbs and another under the nouns.
I am unsure how could I make this transition swifter.

o	Add the interfix ‘-s-‘.

-	Bibliography
Foma - https://fomafst.github.io/
Wiktionary - https://en.wiktionary.org/wiki/Index:Norwegian
Common Norwegian Verbs - https://carla.umn.edu/lctl/materials/norwegian/norwegian-verbs.html
TypeCraft - https://typecraft.org/tc2wiki/Main_Page
Norwegian on the Web - http://www.hf.ntnu.no/now/hardcopies/ShortGrammar.pdf
Norwegian Grammar UCL - https://wiki.ucl.ac.uk/display/ScanStuds/Norwegian+Grammar
Learn Norwegian Naturally - https://www.learnnorwegiannaturally.com/
Morphological Awareness in Norwegian Pre-schoolers - https://www.duo.uio.no/bitstream/handle/10852/64432/Germ-n-Garc-a-Grande_Thesis_Sped4090.pdf?sequence=1&isAllowed=y
Flag Diacritics by Karttunen, L. et al -  http://www.sfs.uni-tuebingen.de/~keberle/FiniteState/Presentations/fsa.fd.pdf
Constraining Separated Morphotactic Dependencies in Finite-State Grammars - https://www.aclweb.org/anthology/W98-1312.pdf
Finite-State Morphology: Xerox Tools and Techniques - http://users.itk.ppke.hu/~sikbo/nytech/gyak/05_morfo/xfst/book.pdf_1.pdf
Computational Modeling of Verbs in Dene Languages: The Case of Tsuut’ina - http://altlab.artsrn.ualberta.ca/wp-content/uploads/2017/05/ComputationalModelingofVerbsinDeneLanguages_170402.pdf
