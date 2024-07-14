# Information-Retrieval-Minimal-System
Information Retrieval across type agnostic documents using Boolean Query and Inverted Index along with Context Sensitive Spelling Correction

# Document Preprocessing and Inverted Index Construction

This project includes scripts to preprocess various document types and construct an inverted index to support boolean queries. The steps below outline the functionality and usage of the code provided.

## Dependencies

First, install the necessary Python libraries: `python-docx`, `pypdf2`, `pandas`, and `nltk`.

## Download NLTK Resources

The code requires some resources from the NLTK library, including tokenizers, stopwords, and wordnet. These can be downloaded using the `nltk.download()` function.

## Preprocessing Functions

### `preprocess_text(text)`

This function converts the input text to lowercase, tokenizes it into words, removes stopwords and punctuation, and then lemmatizes the tokens to reduce them to their base forms.

### Document Reading Functions

- `read_txt(file_path)`: Reads the content of a text file.
- `read_pdf(file_path)`: Extracts text from each page of a PDF file.
- `read_docx(file_path)`: Reads the text from a DOCX file by concatenating the content of all paragraphs.
- `read_xlsx(file_path)`: Reads all sheets from an XLSX file and concatenates their content.

### `preprocess_document(doc_path)`

This function determines the file type (TXT, PDF, DOCX, or XLSX), reads the document accordingly, and preprocesses the text using the `preprocess_text()` function.

### `preprocess_documents(documents_path)`

This function iterates through all supported documents in a directory, preprocesses each one, and stores the results in a dictionary with the document ID as the key and the preprocessed tokens as the value.

## Example Usage

Specify the directory containing your documents and call `preprocess_documents()` to preprocess them. The preprocessed documents are then printed with their respective tokens.

## Inverted Index Construction

### `construct_inverted_index(documents_path)`

This function constructs an inverted index from the preprocessed documents. It maps tokens to document IDs and their positions within the documents. A dictionary mapping document IDs to their filenames is also created.

## Example Usage

Specify the directory containing your documents and call `construct_inverted_index()` to build the inverted index and document ID mapping.

## Boolean Query Function

### `boolean_query(query, inverted_index, doc_id_mapping)`

This function executes boolean queries on the inverted index. It supports tokens like `AND`, `OR`, and `NOT` to combine search terms and find documents matching the query.

## Example Usage

Define your queries and call `boolean_query()` to retrieve the matching document IDs. The results can be mapped back to filenames using the document ID mapping.

## Context-Sensitive Spell Correction

### `context_sensitive_spell_correction(text, vocabulary)`

This function performs context-sensitive spell correction on the input text. It preprocesses the text, checks for misspelled words based on a given vocabulary, generates candidate corrections, and ranks them based on the context within the text.

## Example Usage

Define your vocabulary and input text, then call `context_sensitive_spell_correction()` to obtain the corrected text.

