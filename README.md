# Polis Data Project ----
    This is a pilot project utilizing OCR and LLM prodecures to produce a consistent dataframe from the ennumerated text entries of ancient greek city-states (poleis)

## Overview ----
    The polis data project (PDP) is a collaboration between Aarhus University's Center for Humanities Computing (CHC) and Social Resilience Lab (SRL). The aim of this project is to develop a pipeline for extracting data from the text of archaeological records into a dataframe format. This development is focused on Hansen & Nielsen's "An Inventory of Archaic and Classical Poleis" (2004), but an ideal product would be flexible and applicable to parse the dense, text-heavy nature of any archaeological compilation

## Resource links ----

    Pipeline code: https://github.com/broemelt/polis_data_project
    Data from pattern extraction: https://huggingface.co/datasets/broemelt/PDP_extraction
    Data from LLM: https://huggingface.co/datasets/broemelt/PDP_llm_schema


## Installation ----
    %pip install docling onnxruntime rapidocr-onnxruntime easyocr opencv-python-headless outlines transformers torch anthropic

    import cv2
    import numpy as np
    import torch
    import re
    import os
    import pandas as pd
    import csv
    import json
    import outlines
    import anthropic
    import getpass

    from pathlib import Path
    from tqdm.notebook import tqdm
    from transformers import AutoTokenizer, AutoModelForCausalLM
    from pydantic import BaseModel
    from outlines import from_transformers, Generator, disable_cache
    from docling.datamodel.accelerator_options import AcceleratorDevice, AcceleratorOptions
    from docling.datamodel.base_models import InputFormat
    from docling.document_converter import DocumentConverter, PdfFormatOption
    from docling.datamodel.pipeline_options import (PdfPipelineOptions, TableStructureOptions)

## Usage in 3 phases ----
    1. Preproccesing from PDF source to cleaned text with all poleis identified
        - Addresses font, text, and spacing errors in OCR output
    2. Chunk cleaned text into individual MD files per polis entry
        - Removes unnessessary forword and bibliography sections from all regions so only the entries remain
    3. Define the data schema with in LLM propmt, and process entries to a final dataframe
        - Currently uses Claude API for processing speed

## Requirements ----
    Python 3.12.3
    anthrpoic

## Contributing ----
    This pilot version is tailored to process Hansen & Nielsen's "An Inventory of Archaic and Classical Poleis" (2004). A great improvement would be to continue moving the process closer to an ability to take in any pdf an output desired data categories

    Docling OCR did not detect headers and footers. Experimaenting with other OCRs may improve initial text clarify and reduce need for cleaning and pattern detection

## License ----
    TBD