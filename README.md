[![Tests](https://github.com/librairy/claimer/actions/workflows/tests.yml/badge.svg)](https://github.com/librairy/claimer/actions/workflows/tests.yml)
[![Downloads](https://static.pepy.tech/badge/claimer)](https://pepy.tech/project/claimer)
[![Current Release Version](https://img.shields.io/github/release/librairy/claimer.svg?style=flat-square&logo=github)](https://github.com/librairy/claimer/releases)
[![pypi Version](https://img.shields.io/pypi/v/claimer.svg?style=flat-square&logo=pypi&logoColor=white)](https://pypi.org/project/claimer/)
# librAIry Claimer

## Introduction

Claimer is our cutting-edge tool designed to revolutionize the process of analyzing textual paragraphs and extracting verifiable claims. By leveraging state-of-the-art techniques, we have created a method that breaks down complex text into individual statements that can be fact-checked and validated. 

This powerful tool aims to enhance information comprehension, promote critical thinking, and support researchers, journalists, and fact-checkers in their pursuit of accurate and reliable information. With its advanced capabilities, our tool opens new avenues for assessing claims and fostering transparency in an ever-expanding digital landscape.

## Installation

To install the package, run:
```bash
pip install claimer
```

Afterwards, some resources must be downloaded. This can be either be done by manually calling

```bash
python -m spacy  download  en_core_web_md
python -m spacy_entity_linker "download_knowledge_base"
```

## Use

```python
from claimer import paragraph # version 3.5

# prepare a paragraph
text = "Face masks don’t work. Science in this area has evolved during the outbreak, the body of scientific evidence that has built up shows that the risk of transmission is made lower by wearing a face covering.  The more we learn about COVID-19 the clearer it is that face coverings are an absolute vital tool in our fight against the virus. They effectively capture droplets, which is the main way the virus travels from person to person. According to the British Medical Association, if you don't wear it and have COVID-19, the risk of spreading it to others can be as high as 70%. If you do wear it, the risk drops to 5%. Make sure you wear it in all public indoor spaces and whenever you can't keep a 2m distance from others. Use a face covering is simple and easy way we can all stop the spread of the virus.",

# retrieve the claims
claims = paragraph.get_claims(text)

# iterates over claims 
for i,claim in enumerate(claims):
    print(f"{i}) {claim}")

# OUTPUT:
# 0) Face masks don’t work.
# 1) Science in this area has evolved during the outbreak, the body of scientific evidence that has built up shows that the risk of transmission is made lower by wearing a face covering.
# 2)  The more we learn about COVID-19 the clearer it is that face coverings are an absolute vital tool in our fight against COVID-19 .
# 3) face coverings effectively capture droplets, which is the main way COVID-19 travels from person to person.
# 4) According to the British Medical Association, if you don't wear face coverings and have COVID-19 , the risk of spreading it to others can be as high as 70%.
# 5) If you do wear face coverings , the risk of spreading it to others drops to 5%.
# 6) Make sure you wear face coverings in all public indoor spaces and whenever you can't keep a 2m distance from others.
# 7) Use a face covering is simple and easy way we can all stop the spread of COVID-19

```

## Note

The Claimer at the current state is still experimental and should not be used in production mode.
