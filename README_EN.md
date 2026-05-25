## RFC: Unicode Arabic Script Optimization — Reduction to Functional Core Forms
* Author: Abdurrahman Cevik
* License: MIT
* Status: Proposal / Request for Comments

## 1. Abstract
The current Unicode encoding standard for the Arabic script (including Ottoman Turkish, Kurdish, Persian, and Urdu extensions) treats the contextual variants of characters—namely Isolated, Initial, Medial, and Final forms—as distinct glyph presentations mapped to different code points (specifically within the Arabic Presentation Forms-A and B blocks).
This proposal demonstrates that the historical and structural nature of the Arabic script does not inherently possess four distinct architectural forms per letter. Instead, the script relies on a fundamental binary morphology (Core Form and Terminal Form). This document proposes a technical reform to optimize digital text rendering, reduce data payload in Natural Language Processing (NLP), and streamline font engineering by shifting the contextual shaping logic from legacy font tables directly into logical character stream operations.

---
## 2. The Core Problem: The Legacy "Four-Form" Illusion
For decades, digital operating systems and text rendering engines have operated under the assumption that Arabic characters require four separate encodings based on their position in a word. This approach is a legacy artifact derived from mechanical moveable-type printing presses and early digital typesetting limitations, rather than the intrinsic grammar of the script.
Maintaining four separate visual states for a single character causes several systemic inefficiencies:

* Font Payload Inflation: Type designers must redundantly map and draw multiple contextual duplicates of the same phonetic root.
* NLP & Tokenization Overhead: Machine learning models, Large Language Models (LLMs), and tokenizers consume unnecessary computational resources analyzing positional variants rather than purely semantic roots.
* Rendering Bugs: Diacritics (such as Harakat/Vowel signs) frequently misalign, detach, or distort during cross-platform text rendering due to complex GPOS/GSUB OpenType lookups.

---
## 3. The Proposed Mathematical Model: 1 and 2 Form Reduction
An anatomical analysis of the script reveals that characters naturally fall into two strict structural categories, eliminating the need for the four-form legacy system.
## Category A: The Immutable Invariant (1 Form)
Letters such as Elif (ا), Dal (د), Zal (ذ), Ra (ر), Ze (ز), and Vav (و) never connect to the subsequent character leftward.

* Current System: Forced to adapt to positional logic unnecessarily.
* Proposed System: These characters possess exactly one invariant form. They are represented by a single universal code point across the entire text stream, regardless of position.

## Category B: The Fluid Continuous (2 Forms)
All remaining connecting characters possess exactly two morphic states:

   1. The Continuous/Flow Form (Core): The primary root state of the letter that naturally extends to connect with the next letter (e.g., بـ). In the proposed system, this is the default state of the character in the standard code chart (0x06 block).
   2. The Stationary/Terminal Form (End): The state assumed when the character concludes its connection, capping the stroke (e.g., ب).

---
## 4. Technical Implementation: The Boundary Operator Mantissa
Instead of embedding four pre-rendered positional glyphs into Unicode space, the proposed model utilizes a Stream Boundary Operator (akin to a structural delimiter or terminal marker) to handle contextual rendering dynamically.

* Default Behavior: The text engine renders characters in their continuous/flow form by default. The letters naturally flow into one another as a single cursive stroke.
* The Break Rule: When a word ends, or when a non-connecting boundary is reached, a logical operator triggers the character to shift into its Terminal Form.

## Conceptual Example:
Instead of mapping:<br>
<b>[Initial B] + [Medial B] + [Final B] + [Space] + [Isolated B]</b><br>
The proposed data stream processes:<br>
<b>[Core B] + [Core B] + [Core B] + [Terminal Boundary] + [Space] + [Terminal Boundary]</b><br><br>
This approach shifts the responsibility of script connection from static font tables to fluid, algorithmic text flow, drastically reducing the data storage required to represent cursive text accurately.

---
## 5. Societal and Industrial Benefits

* Computational Efficiency in AI: Text data size shrinks significantly, allowing faster text processing and lower token consumption for Arabic-script based Artificial Intelligence applications (NLP/LLM).
* True Cursive Fidelity: This model restores the digital script to its absolute historical origin—the continuous flow of the pen—bridging the gap between classical calligraphy and modern screen technology without sacrificing typographic aesthetics.
* Universal Accessibility: Simplifying the character matrix lowers the barrier to entry for developing localized software, screen readers, and digital archiving tools across the Islamic world.

---
