# CLI Reference: DNA-to-Protein Translation Tool

  

This reference manual provides detailed syntax, argument specifications, and error handling definitions for the `dna_translate.py` command-line utility. This tool is designed to transcribe DNA sequences into RNA and translate them into functional peptide strings.

  

---

  

## Command Syntax

  

Execute the utility from your terminal using the following baseline structure:

  

```bash

python3 -m bio_tools.dna_translate --input [FILE_PATH] [FLAGS]

```

  

---

  

## Positional Arguments

  

| Argument | Type | Description | Required |

| :--- | :--- | :--- | :--- |

| `--input`, `-i` | `String` | Relative or absolute path to the target sequence file (`.txt` or `.fasta`). | **Yes** |

| `--output`, `-o` | `String` | Destination path where the translated amino acid sequence will be written. | No |

  

---

  

## Operational Flags

  

### `--transcribe-only`

* **Type:** Boolean (Switch)

* **Description:** Halts the execution pipeline immediately after generating the intermediate messenger RNA (mRNA) string. Does not convert the sequence into amino acids.

* **Example:**

  ```bash

  python3 -m bio_tools.dna_translate -i sample.fa --transcribe-only

  ```

  

---

  

## System Error and Exception Handling

  

The utility evaluates incoming genomic strings for data integrity before execution. Below are the standard exit codes and error matrices:

  

### `ERR_INVALID_NUCLEOTIDE`

* **Trigger Condition:** The input sequence contains characters outside the valid biological IUPAC alphabet (`A`, `C`, `G`, `T`, `N`).

* **Console Output:**

  ```text

  CRITICAL: Execution halted. Invalid nucleotide token 'X' detected at position 142.

  ```

* **Remediation:** Scrub the input dataset to eliminate corrupted sequencing artifacts or laboratory annotations.