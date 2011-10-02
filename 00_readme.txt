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
   --> DONE by Trond

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

______________________________________

1. oahpalemmas_not_in_fin.txt has been transformed into oahpalemmas_not_in_fin.xml
   and then split by different pos files: check add2src dir for them.

Note: Although Trond claimed that there is no need to have pos in the csv file,
      there has been an xxx_smafin.xml file generated, and this means that no pos values
      have been found in the smanob files. Why?

2. Check double entries: see smafin-test-results.xml ==> done


3. resolve the pos ambiguity in the add2src dir: a_adv_smafin.xml ==> done

=============
Unification: smafin dict files with smanob oahpa files

a. the entry in the oahpa file has more than one meaning group
   ==> marking for manual desambiguation by
       oa_unify="todo" (which has to be change after unification into
       oa_unify="done")

b. the entry in the smafin-dict file has more than one t-element:
   ==> take the first and mark it with stat="pref"
       (a manuall check would be strongly recomended)

   <e>
      <lg>
         <l pos="a">göögkeles</l>
      </lg>
      <mg>
         <tg>
            <t pos="a">upea</t>
            <t pos="a">mainio</t>
         </tg>
      </mg>
   </e>


The automatic unification of adj from both add2src and src dirs is done.
Entries to be fixed manually are marked as agreed with the flag oa_unif="todo".

a_smanob.xml:
  automatically ==> done
src>grep _FIN a_smanob.xml | wc -l 
      56
  manually ==> done

adv_smanob.xml: 
   automatically ==> done
src>grep _FIN adv_smanob.xml | wc -l
      13
  manually ==> todo

