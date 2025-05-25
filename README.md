# CATnaPS
Computer Assisted Tools for [choose your acronym] Patristics Scholars
aka *Ancient Christian Texts and Comparanda in BGM CSV format*

## Purpose

This repository prunes down openly available, complex syntactical treebanks (XML and CoNNL-U) into simple CSV files in the BGM (BibleWorks Greek Morphology) format, i.e., a condensed form of the encodings first developed by the Computer Assisted Tools for Septuagint/Scripture Studies at the University of Pennsylvania.

Essentially, texts are presented in their normal running sequence, but each word is split into two parts, and a "@" delimiter is put between them, kind of like an email address. 
The part to the left of the "@" symbol is the standard dictionary word form (lemma).

The part to the right is the one to seven character BGM morphological tag describing the word form (part of speech, person, number, tense, mood, voice, gender, case, and degree). A [key to the BGM schema](https://doi.org/10.5281/zenodo.10066745) is available on Zenodo.

This format has several advantages for computational linguistics research:
- it reflects the internal reference structure of documents (e.g., books, sections, chapters, verses, line numbers), making it easier to correlate with human readable editions and translations
- it encodes a lot of information in a compact amount of space, achieving smaller file sizes and quicker query results
- it omits punctuation and other symbols such as brackets and parentheses, preserving only root word forms (lemmata) and morphological tags as connected tokens
- it allows for a range of searches, from simple word searches to more advanced regex searches of multiple word strings and morphological patterns
- it simplifies document retrieval and identification by providing just one file per document

These advantages are shared with the AGDTiny repository. But the BGM data may be easier for many to use, can usually be searched with shorter and less complex regex strings, and its strings lend themselves more easily to citation in scholarly publications.

## File and Directory Names and Structures

To avoid confusion and to participate in the linked open data movement, this corpus uses Canonical Text Service uniform resource names (cts_urn) for documents and folder structures, just like the Perseus Digital Library, the Patristic Text Archive, etc. These identifiers take a little getting used to, but trust, they help everyone stay organized and on the same page.

All cts_urn compliant documents sit within a "data" directory. 

Within the "data" directory, a separate subfolder is created for each author or collection.

> *Plutarch, for example, is tlg0007. The New Testament is tlg0031.*

Within those directories, separate subdirectories are created for each work.

> *The Gospel of Matthew is located in the tlg001 subfolder of the New Testament folder tlg0031.*

All document filenames use this author.work composite key as a prefix, with periods placed between fields and after the composite key.

> *The Gospel of Matthew has the composite cts_urn identifier tlg0031.tlg001.*

The middle part of the filename identifies the project or group, in our case, "bgm", followed by a hyphen.

> *The Gospel of Matthew within this project is known as tlg0031.tlg001.bgm-*

Finally, the filename suffix reflects the language and version. Currently, Greek is the only language in use, and typically only one version exists for each work.

> *The entire filename for the Gospel of Matthew here is tlg0031.tlg001.bgm-grc1.txt*
 
## Text Structure

Each CSV consists of two columns: location and text.

Locations reflect subdivisions used within the text, such as books, sections, chapters, verses, lines, etc. Locations can be purely numeric or alphanumeric, and subdivisions within a location are always separated by periods.

Text fields contain the running sequence of lemma@morphtag values for each specific location.

For example, the opening verse of the Gospel of Matthew reads:
1.1,βίβλος@nnfsc γένεσις@ngfsc Ἰησοῦς@ngmsp Χριστός@ngmsp υἱός@ngmsc Δαυίδ@ngmsp υἱός@ngmsc Ἀβραάμ@ngmsp

A key to the BibleWorks Greek Morphology is available on Zenodo.

## Character Encoding

All characters are Unicode (UTF-8) and composed (NFC). Thus each character corresponds to a single Unicode endpoint. Because words are lemmatized (put in their root forms), accents and breathing marks are standardized, preventing issues with Greek words not matching due to different or inconsistent accenting and sentence punctuation.

## Data sources

The main data source for this repository is my AGDTiny repository, with the main difference being that AGDTiny uses the standard AGDT morphological tags, rather than the simpler, more compressed CATSS/BGM morphological tags.

The AGDTiny repository, in turn, is derived largely from version 0.2.0 of the Opera Graeca Adnotata, curated by Giuseppe Celano at the University of Leipzig, archived at [Zenodo](https://doi.org/10.5281/zenodo.14206061) on 2024-11-24, and distributed under a CC BY-SA 4.0 license allowing for Sharealike reuse.

Additional works will likely be added from the GLAUx corpus if they are 1) not present in OGA and 2) have licenses sufficiently permissive to allow for reuse.

The OGA and GLAUx corpora were in turn derived from several major corpora of digital editions of classical Greek texts, most notably the [Perseus Project](https://github.com/PerseusDL/canonical-greekLit) (Department of Classics, Tufts University) and closely connected [First1KGreek](https://github.com/OpenGreekAndLatin/First1KGreek) project. First1KGreek is funded by the "Harvard Library Arcadia Fund, European Social Fund, and the Alexander-von-Humboldt professorship for Digital Humanities at Leipzig. The data has been produced in an international cooperation with the Center for Hellenic Studies, the Harvard Library, Mount Alison University, Tufts University, the University of Leipzig, and the University of Virginia." Significant contributions, particularly to Patristic and early Christian literature, were made available to OGA through the [Patristic Text Archive](https://github.com/PatristicTextArchive/pta_data) thanks to funding from Academies Programme and housed at the Berlin-Brandenburg Academy of Sciences and Humanities. Contributions of digital editions and most of the canonical text service ontology come by way of the famous [Thesaurus Linguae Graecae](https://stephanus.tlg.uci.edu/index.php#login=true) centered at the University of California, Irvine.

OGA annotation includes morphosyntactical features based on the as well as data (sometimes provisional) pertaining to authorship and likely date or date range of composition.

Elsewhere I have archived a [simple comparison of documents in the OGA and GLAUx corpora](https://doi.org/10.5281/zenodo.14254072), which shows at a glance which documents are unique to OGA, which are unique to GLAUx, and which texts overlap between the two.

## Citation

The OGA corpus was described in this earlier article that corresponds to v0.1.0, which is the preferred publication for citation.

> Celano, Giuseppe A. "Opera Graeca Adnotata: Building a 34M+ Token Multilayer Corpus for Ancient Greek". arXiv cs.CL. 2024-03-14. https://doi.org/10.48550/arXiv.2404.00739.

The GLAUx corpus was described in this earlier article:

> Keersmaekers, Alek (2021): The GLAUx corpus: methodological issues in designing a long-term, diverse, multi-layered corpus of Ancient Greek. *Proceedings of the 2nd International Workshop on Computational Approaches to Historical Language Change 2021*, 39–50. Online: Association for Computational Linguistics. doi:10.18653/v1/2021.lchange-1.6.

To cite this repository specifically, and/or to access its archival version on Zenodo, see:
> Bilby, Mark G. "CATnaPS: Searchable and Citable Strings of Ancient Greek Lemmata and Morphological Tags". Release 0.2.0. 2025-05-22. doi: [10.5281/zenodo.15508287](https://doi.org/10.5281/zenodo.15508287)
