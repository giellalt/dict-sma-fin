Todo:
I. pos info in the xml file:
   compare lemma form with lemmata from the existing smaX files
   when adding data to the existing sma_oahpa

 - possible problems: 
  1. lemma found in smaoahpa files but with different pos values
  2. lemma found with exactly one pos value but potentially different values
  3. lemma not found

No lemma found in the existing source files for smaoahpa:
src>grep '<poses/>' out_00/smafin.xml.xml | wc -l
     692

Lemma found in the existing source files for smaoahpa:
src>grep '<poses>' out_00/smafin.xml.xml | wc -l 
    1857

Ambiguous pos assigning according to the data found in smaoahpa files:
rc>grep count out_03/smafin.xml.xml | wc -l 
      11

Adding pos from ped/sma/src/*.xml files to the xml-transformed smafin file
both to the lemma AND to all translations. The assumption hereby is that
in most of cases the pos values are the same. --> DONE

TODO:
 - check and correct pos values for the ambiguous pos: e.g., pos="a_n"
 - check and if needed correct pos values in both l and t elements


II. cleanup entries

III. CLT have to agree on a common practice when working with inc-files and xml-files
generated from csv inc-files.
 1. I proposed that inc-files should be the very original ones, this implies that
    they should NOT be changed.
 2. Why not to work with the xml-transformed data if already there?

 3. If the inc-file are changed then at least the structure should be kept.

Legend for the field separators in xxx_smafin.txt file:

___ (instead of TAB) = separates each main column such as lemma, translations, comments, possible pos, etc.

$ (instead of ;) = separates meaning groups in the translation column

| (instead of ,) = separates translations within a meaning group

Examples:
aktine ___ yhdessä
amma ___ toki $ pas | päs
askedh ___ kuutamo | kuunloiste
asvedihks ___ pelottava | kauhea
baahkes ___ lämmin
baahtjetje ___ pikkupoika
baakohth ___ sanaton ___ USIKKER
baaktoe ___ kautta | ohitse
baalte ___ sivulla | vieressä $ ohi

Please keep it like that!

