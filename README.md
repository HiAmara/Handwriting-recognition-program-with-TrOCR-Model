# Handwriting and Text recognition program with [TrOCR](https://huggingface.co/docs/transformers/model_doc/trocr) Model
Seminar Paper with KIT AIFB: Automated Extraction of Exam Information: An image to text Program for Efficient Student and Score Recognition

## Motivation

At University, lecturers and tutors routinely spend hours manually digitizing graded paper exams by transcribing final scores, individual exercise points, and student information into Excel spreadsheets by hand. This project was motivated by the goal of speeding up that process by automatically recognizing and extracting this information, the only remaining human task is a final verification.

## Overview

This project automates the extraction of information from exam title sheets using machine learning and computer vision. It combines handwritten text recognition with automatic table/text localization to turn photographed exam sheets into editable data.

## What it does

1. **Capture** — takes an image of an exam title sheet
2. **Detect** — locates the relevant table/text regions using OpenCV contour detection and hierarchy-based filtering
3. **Recognize** — extracts handwritten text (student name, student ID, points) using **TrOCR**, a Transformer-based OCR model
4. **Validate** — matches OCR output against a reference participant list using fuzzy string matching (Levenshtein distance via FuzzyWuzzy) to correct for OCR errors
5. **Review & Edit** — presents results in a simple **FastAPI**-based interface for manual correction
6. **Export** — saves the final, verified data to an Excel file

<div style="display: flex; justify-content: space-around;">
  <img src="photos/program interface" alt="Image 1" style="width: 70%;">
  <img src="photos/physical program setup" alt="Image 2" style="width: 28%;">
</div>

## Tech Stack

- **OpenCV** — image preprocessing, contour detection, text/table localization
- **TrOCR** — handwritten text recognition (image-to-text)
- **FuzzyWuzzy** — approximate string matching for validating OCR results against known student data
- **FastAPI** — web interface for capturing, reviewing, and editing extracted data
- **Excel export** — final structured output

## Status & Future Work

This is a seminar project / proof of concept. Planned improvements include:
- Fine-tuning TrOCR on real exam sheet snippets (especially numeric fields) for higher accuracy
- Automated (adaptive) threshold calculation for more robust image binarization
- More robust perspective correction for imperfectly captured document images

## Privacy Note

All processing and data storage happened locally, avoiding upload of sensitive student information to external services.
