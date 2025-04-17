# 🔐 CUPP (Common User Passwords Profiler) - Function Documentation

CUPP is a Python tool used to generate personalized wordlists for password cracking or penetration testing.
It works by taking user-provided profile information (e.g., name, birthdate, spouse, etc.) and producing a
highly customized list of password guesses based on common patterns like name+year, leetspeak, pet names,
and more.

------------

You need Python 3 to run CUPP.

Quick start
-----------

    $ python3 cupp.py -h

## Options

  Usage: cupp.py [OPTIONS]

        -h      this menu

        -i      Interactive questions for user password profiling

        -l      Download huge wordlists from repository

        -a      Parse default usernames and passwords directly from Alecto DB.
                Project Alecto uses purified databases of Phenoelit and CIRT which where merged and enhanced.

        -v      Version of the program

---

### Example video

![cupp-example](screenshots/cupp-example.gif)

## Global Variables

### `CONFIG`

A global dictionary that stores configuration loaded from `cupp.cfg`. It contains:

- `global`: year ranges, special characters, word length limits, etc.
- `LEET`: mappings for leetspeak substitutions (e.g., `a → 4`, `e → 3`).
- `Other`: options like links to download dictionary.

---

## 🔧 Function Reference

### `read_config(filename)`

Reads the `cupp.cfg` configuration file and fills the `CONFIG` dictionary with values.

- Parses sections like `[years]`, `[specialchars]`, etc.
- Loads leetspeak mappings into `CONFIG["LEET"]`.

### `make_leet(x)`

Converts a given string `x` into leetspeak using the `CONFIG["LEET"]` mapping.

### `concats(seq, start, stop)`

Generates strings by appending a range of numbers to each string in `seq`.

### `komb(seq, start, special="")`

Yields combinations of `seq + special + start` elements.

### `print_to_file(filename, unique_list_finished)`

Saves a sorted password list to a file and optionally prints it with animations.

### `print_cow()`

Prints a fun ASCII cow banner with program branding.

### `version()`

Displays the current version of CUPP with credits.

### `improve_dictionary(file_to_open)`

Enhances an existing wordlist by applying transformations like:

- Leet mode
- Special chars
- Random number suffixes
- Word concatenations

### `interactive()`

Prompts the user for profile data interactively and passes it to the generator.

### `generate_wordlist_from_profile(profile)`

Generates a highly customized password wordlist using profile details. Applies:

- Names + years
- Special characters
- Reversed words
- Leet transformations
- Length filtering

### `download_http(url, targetfile)`

Downloads a file from a URL to the local filesystem.

### `alectodb_download()`

Downloads and extracts default credentials from the Alecto database.

### `download_wordlist()`

Displays a list of wordlist categories and lets the user download them.

### `download_wordlist_http(filedown)`

Downloads multiple dictionary files from selected category folders.

### `mkdir_if_not_exists(dire)`

Creates a directory if it doesn't already exist.

### `main()`

Central controller that parses CLI arguments and triggers the appropriate function.

### `get_parser()`

Builds and returns an argparse parser with all CLI options.

### `test_cupp.py`

- This script is spacially made for Devlopers it will be useful for testing CUPP's core functions so devlopers can be sure that after updating it the script wouldn't break

---

## 🧪 Entry Point

```python
if __name__ == "__main__":
    main()
```

---

## ✅ Summary

CUPP is a customizable wordlist generator that takes advantage of personal profiling and pattern-based logic to create realistic, target-specific password lists. It includes features like:

- Leetspeak transformation
- Random number and special char appending
- Wordlist improvement
- Alecto database integration
- Wordlist download from public

## Scope of Improvement

- Updating it from CLI to GUI using libraries like `Tkinter`.
- This tool can be integrated with other data scraping tools like `SpiderFoot` and `Recon-ng`.

## [ Team Members ]

| Name              | Roll Number                                | Group       |
| ----------------- | ------------------------------------------ | ----------- |
| **Rudra Patel**   | [202404028](mailto:202404028@daiict.ac.in) | G6 (Leader) |
| **Pranav Patel**  | 202404051                                  | G6          |
| **Devanshi Modi** | 202401498                                  | G6          |
| **Deep Sutariya** | 202401219                                  | G4          |
