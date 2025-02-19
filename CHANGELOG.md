# Changelog

## Version 0.4.5 - 2022-12-07

- Basic Synthesizer: Do not synthesize zeros since prefixed and suffixed zeros are often stripped in amounts. E.g. 
`2340.00` might be synthesized to `0432.22` which should've been written `432.22` but we can't detect this. Another 
example would be if the value in ground truth is `2340.00` and in the PDF it is written as `2340`. If we synthesize
to `0432.22` in the ground truth, we'll have the incorrect amount of `0432` in the PDF.

## Version 0.4.4 - 2022-12-07

- Do not trust font character mappings in PDF, instead scan PDF for all printed characters when determining which 
characters are available for synthesizing

## Version 0.4.3 - 2022-11-29

- Added timeout to PDF synthesizing

## Version 0.4.2 - 2022-11-25

- Additional usage of typing library

## Version 0.4.1 - 2022-11-24

- Using typing library in `synthetic/core/synthesizer.py`
- Fixed indentation of docstring in `synthetic/image/poisson_blending.py`

## Version 0.4.0 - 2022-08-05

- Added image synthesizing. To use image synthesizing you need to also provide bounding boxes in the ground truth JSON for each label.

## Version 0.3.8 - 2022-08-08

- Bugfix: mismatch between ground truth and document on subsequent runs targeting the same directory

## Version 0.3.5 - 2022-06-27

- Now catching additional exceptions that might occur when synthesizing PDFs.

## Version 0.3.1 - 2022-05-27

- Now checking `dst_dir` for existing files to avoid processing already processed PDFs.
- Added optional `--max-fonts` to specify the maximum number of fonts a PDF can contain for synthesizing. PDFs breaching the threshold will be discarded.

## Version 0.3.0 - 2022-05-19

- Added optional `--num-outputs-per-document` to specify how many output PDFs to create per input PDF
- Added optional `--max-pages` to specify the maximum number of pages a PDF can contain for synthesizing. PDFs breaching the threshold will be discarded.

## Version 0.2.2 - 2022-05-12

- Save new PDFs in compressed non-qpdf mode
