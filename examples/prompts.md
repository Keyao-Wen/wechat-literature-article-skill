# Example Prompts

## Chinese WeChat Article From A Paper PDF

```text
Use $wechat-literature-article to write a Chinese WeChat public-account article from this paper PDF.

Requirements:
- Give the article an eye-catching but rigorous WeChat title.
- Use the standard research-reader length unless the paper requires a longer method-heavy treatment.
- Put the paper title, journal, DOI, and publication date at the beginning.
- Organize the article as abstract, background, data and methods, main results, discussion, and conclusion.
- Explain the data and computational methods in detail.
- Keep terminology consistent throughout the article.
- Internally audit key numbers against the paper's figures, tables, or text before delivery.
- Include the core figures and one important methodological extended figure if available, and explain the meaning of every selected figure.
- Make sure every inserted figure is referenced in the text and every figure mentioned in the text is actually inserted or intentionally omitted.
- Use SimSun/宋体 for Chinese text and Times New Roman for Latin text where practical, with consistent font sizes for same-level headings and body paragraphs.
- Clean Chinese typography, including unnecessary spaces between numbers, units, punctuation, parentheses, and Chinese text.
- Output a Word document suitable for copying into the WeChat editor. Keep internal notes, terminology lists, numeric audit tables, and QA notes out of the publishable Word file.
```

## Revision Of An Existing Draft

```text
Use $wechat-literature-article to revise this draft for WeChat publication.

Please make the language more academic, reduce unnecessary English terms, improve the methods and conclusion sections, keep only publishable content, and check whether figures are cropped cleanly with axes and legends visible.

Also propose a rigorous but attractive title, standardize Word fonts and font sizes, explain each selected figure, and clean Chinese typography issues such as unnecessary spaces around numbers and punctuation.

Keep terminology consistent, audit key numbers internally, check figure-text correspondence, and separate the publishable draft from working notes.
```

## Journal-Club PPT

```text
Use $wechat-literature-article to prepare a journal-club PPT from this paper.

The deck should include paper metadata, research gap, data and methods, main results, mechanism, critique/limitations, and discussion questions. Use one clear claim per slide and include the core figures.
```
