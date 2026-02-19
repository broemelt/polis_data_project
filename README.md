The polis data project (PDP) is a collaboration between Aarhus University's Center for Humanities Computing (CHC) and Social Resilience Lab (SRL). The aim of this project is to develop a pipeline for extracting data from the text of archaeological records into a spreadsheet format. This development is focused on Hansen & Nielsen's "An Inventory of Archaic and Classical Poleis" (2004), but an ideal product would be flexible and applicable to sources from the dense, text-heavy nature of archaeological compilations.

PDP_inventory.csv is the current state of the extraction product. Some errors still remain (a few double entries, text bodies limited to 30k characters due to cell limit)

The extraction code uses Docling OCR on Part 2 (The Inventory) to convert the text from PDF to Markdown for readable inspection of pre-processing necessities:
1. Text is cleaned to address font, text, and spacing errors
2. Unnessessary forword and bibliography sections are removed so that only the poleis entry subsections remain for all 46 region sections
3. Chunk text by a pattern that identifies all 1035 poleis of the inventory
4. Regions names had to be manually listed (OCR did not detect headers and footers)

A simple listing confirms that 100% of poleis have been detected

HN_p2_chunked.md contains all essential text entries (not shared to github due to HN copyright)

The chunked texts are converted into invididual md and json files

The PDP_inventory.csv in made from these json files