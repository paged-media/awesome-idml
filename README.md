# Awesome IDML [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of tools, libraries, applications, services, and resources for working with **IDML — Adobe InDesign Markup Language**.

[IDML](https://www.idml.dev/) is an open, XML-based file format that represents the full content and structure of an Adobe InDesign document. An `.idml` file is a ZIP container (a "package") of XML parts — stories, spreads, master spreads, styles, resources, and metadata — that can be created, inspected, and modified programmatically **without InDesign itself**. This makes IDML the backbone of cross-application interchange, automated/database publishing, localization, and content reuse pipelines.

This list focuses strictly on Adobe InDesign Markup Language. Note that "idML" / "Indented Delimiter Markup Language" packages (e.g. some crates and npm modules) are an unrelated format and are intentionally excluded.

## Contents

- [Specification & Official Resources](#specification--official-resources)
- [Understanding the Format](#understanding-the-format)
- [Libraries & SDKs](#libraries--sdks)
  - [Python](#python)
  - [PHP](#php)
  - [JavaScript & TypeScript](#javascript--typescript)
  - [Rust](#rust)
  - [Java](#java)
  - [XSLT & XProc](#xslt--xproc)
- [Converters & Transformation](#converters--transformation)
- [Applications That Open & Edit IDML](#applications-that-open--edit-idml)
- [Conversion & Preview Tools](#conversion--preview-tools)
- [Database & Automated Publishing](#database--automated-publishing)
- [Creative Automation & Web-to-Print](#creative-automation--web-to-print)
- [Localization & Translation](#localization--translation)
- [Scripting & Automation](#scripting--automation)
- [Related Formats](#related-formats)
- [Books](#books)
- [Articles & Tutorials](#articles--tutorials)
- [Contributing](#contributing)

## Specification & Official Resources

The formal IDML specification and Cookbook were last revised by Adobe for InDesign CS6 (DOM/IDML version 8.0, 2012) and were subsequently removed from Adobe's developer site. The format itself remains stable and forward-compatible, with the `DOMVersion` attribute incrementing per InDesign release.

- [Adobe InDesign Markup Language (IDML) Cookbook](https://community.adobe.com/havfw69955/attachments/havfw69955/indesign/632677/1/IDML_cookbook_9627253.pdf) - The informal "how-to" guide for working with IDML, covering packages, snippets, schema generation, and common recipes (CS6 edition, hosted on the Adobe community forum).
- [IDML File Format Specification (mirror)](https://community.adobe.com/t5/indesign-discussions/where-is-the-idml-specification/m-p/13172633) - Community thread tracking surviving mirrors of the formal CS5/CS6 specification PDFs after Adobe withdrew them.
- [Adobe InDesign SDK](https://developer.adobe.com/console/) - The InDesign Plugin SDK ships IDML documentation and `docs/references/idml-schema.zip`, the place to generate RELAX NG schemas for your plug-in configuration.
- [Automated publishing with XML, IDML & scripting](https://helpx.adobe.com/indesign/automation.html) - Adobe's official entry point for InDesign automation, including IDML and InDesign Server.
- [Adobe InDesign Server](https://helpx.adobe.com/indesign/automation.html) - The robust, scriptable, server-side build of InDesign sharing the desktop codebase — the canonical way to render/round-trip IDML with full fidelity at scale.

## Understanding the Format

- [IDML.dev](https://www.idml.dev/) - A comprehensive, maintained guide to the IDML format: what it is, why it matters, and a part-by-part walkthrough of the package contents. Maintained by Bit&Black.
- [Inside IDML](https://www.idml.dev/en/inside-idml.html) - Detailed breakdown of the `.idml` ZIP structure: `designmap.xml`, `Spreads/`, `Stories/`, `Resources/`, `MasterSpreads/`, `META-INF/`, and `XML/`.
- [IDML — Just Solve the File Format Problem](http://justsolve.archiveteam.org/wiki/IDML) - File-format wiki entry with historical context, MIME type, and relationship to INX.
- [Where is the IDML specification?](https://community.adobe.com/t5/indesign-discussions/where-is-the-idml-specification/m-p/13172633) - Long-running Adobe community discussion that is, in practice, the best living reference on spec availability and schema generation.

## Libraries & SDKs

### Python

- [SimpleIDML](https://github.com/Starou/SimpleIDML) - The most popular open-source IDML library. Reads, edits, splits, merges, and manipulates IDML packages, with optional InDesign Server integration for export to PDF/JPEG/INDD.
- [idml2html-python](https://github.com/roverbird/idml2html-python) - Converter from IDML to HTML (Python and JavaScript variants).
- [outdesign](https://github.com/yanntrividic/outdesign) - A converter bridging IDML and Pandoc, with extensive conversion customization. ([GitLab origin](https://gitlab.com/deborderbollore/outdesign).)
- [idml2docbook](https://github.com/yanntrividic/idml2docbook) - Convert IDML files to DocBook (and other Pandoc targets), with a companion [HTTP server](https://github.com/yanntrividic/idml2docbook-server).

### PHP

- [idml-json-converter](https://github.com/BitAndBlack/idml-json-converter) - Convert IDML into JSON and back, exposing the whole package as an easily navigable/editable array. Includes a CLI.
- [IDMLlib](https://github.com/jorisros/IDMLlib) - Read InDesign IDML files, extract tagged content, convert to HTML, and create/modify IDML. Available via Composer as `jorisros/idml-lib`.
- [markdown-idml-converter](https://github.com/BitAndBlack/markdown-idml-converter) - Convert Markdown into (parts of) IDML files.
- [php-idml (deathlyfrantic)](https://github.com/deathlyfrantic/php-idml) - A simple class for file management of IDML packages.
- [php-idml (xorcare)](https://github.com/xorcare/php-idml) - A lightweight class to handle IDML file management.
- [prometee/php-idml](https://packagist.org/packages/prometee/php-idml) - A minimal Composer package for IDML file handling.
- [IDML Creator / Validator / Writer for PHP](https://www.idml.dev/en/tools.html) - A suite of commercial PHP packages (Bit&Black) for creating, validating, writing, and converting IDML (HTML↔IDML, JSON↔IDML, Markdown→IDML).

### JavaScript & TypeScript

- [imgly/idml-importer](https://github.com/imgly/idml-importer) - Import IDML files into the IMG.LY Creative Editor SDK (CE.SDK), enabling browser-based editing of InDesign layouts.
- [DeepIDML](https://github.com/Heng-xiu/DeepIDML) - A parser focused on extracting information from IDML, including converting InDesign styles to JSON and CSS.

### Rust

- [idml-to-pdf](https://github.com/ch1nq/idml-to-pdf) - An IDML parser written in Rust (quick-xml + serde) that aims to generate PDFs comparable to InDesign's own export, using LibHaru.

### Java

- [Apache Tika — IDMLParser](https://tika.apache.org/3.0.0/api/org/apache/tika/parser/indesign/IDMLParser.html) - Tika's built-in parser for extracting text and metadata from IDML documents as XHTML SAX events. Useful for indexing, search, and content pipelines.

### XSLT & XProc

- [transpect/idml2xml](https://github.com/transpect/idml2xml) - Convert IDML to Hub XML or extract tagging from an IDML file; the core of the transpect toolchain.
- [transpect/idml2xml-frontend](https://github.com/transpect/idml2xml-frontend) - Frontend that converts InDesign IDML to XML (e.g. DocBook).
- [idml_docx-to-docbook_epub-demo](https://github.com/transpect/idml_docx-to-docbook_epub-demo) - XProc demonstration pipeline converting IDML/DOCX into DocBook and EPUB.

## Converters & Transformation

- [outdesign](https://github.com/yanntrividic/outdesign) - IDML ↔ Pandoc bridge for converting between IDML and dozens of document formats.
- [idml2html-python](https://github.com/roverbird/idml2html-python) - IDML → HTML extraction.
- [markdown-idml-converter](https://github.com/BitAndBlack/markdown-idml-converter) - Markdown → IDML generation.
- [g16WPIDML](https://github.com/ghifari160/g16WPIDML) - Generate a WordPress post from an InDesign document via IDML.
- [transpect](https://github.com/transpect) - A complete open-source XML transformation framework with mature IDML import/export, widely used in scholarly and book publishing.

## Applications That Open & Edit IDML

Because IDML is an open, documented format, a growing number of layout and design applications can read it directly — letting you open, edit, and (in some cases) round-trip InDesign documents without an InDesign license. Capability varies: most apps **import** IDML, while only a few can also **export** it back to InDesign. Fidelity is rarely 100% — complex tables, effects, and drop caps may need cleanup — but for most layouts these tools are very usable.

- [Adobe InDesign](https://www.adobe.com/products/indesign.html) - The origin of the format. **Imports and exports** `.idml` ("InDesign Markup"), the canonical reference implementation and primary route for cross-version interchange.
- [VivaDesigner](https://viva.systems/) - High-end DTP app (desktop, web, and server editions) that both **imports and re-exports** IDML (InDesign CS4 / v6 and later), enabling near loss-free, two-way exchange with InDesign — rare among third-party tools. Supports working in parallel with InDesign and returning documents to it.
- [Affinity Publisher](https://affinity.serif.com/publisher/) - Serif's professional layout app **imports** IDML (v1.8 and later), the main path for moving InDesign work into the Affinity suite (macOS, Windows, iPad).
- [QuarkXPress](https://www.quark.com/products/quarkxpress) - Long-standing professional DTP application that **imports** IDML, allowing InDesign layouts to be opened and edited in Quark.
- [Scribus](https://www.scribus.net/) - The leading free, open-source DTP application (Windows, macOS, Linux, BSD, ChromeOS). **Imports** IDML (1.4.x onward, substantially improved in 1.6.0) and exports print-ready PDF — a popular no-cost way to view IDML, generate layout previews, and check translated files.
- [Canva](https://www.canva.com/) - The web-based design platform can exchange with IDML via the [ConvertMarkz](https://markzware.com/convertmarkz/) app in the Canva marketplace, which exports Canva designs to IDML (and InDesign, Affinity, QuarkXPress) and back.

## Conversion & Preview Tools

- [Markzware IDMarkz](https://markzware.com/products/idmarkz/) - Standalone macOS app to preview INDD files and convert/export them to IDML, QuarkXPress, Affinity Publisher, older InDesign, PDF, and image formats — no InDesign required.
- [Markzware IDMarkz SE](https://markzware.com/products/idmarkz_se/) - The Windows edition of IDMarkz, focused on INDD → IDML and other DTP targets, with scriptable automation.
- [Markzware OmniMarkz](https://markzware.com/products/) - Combines Markzware's conversion tools into a single desktop app, including export to IDML and JSON.
- [Markzware PDFMarkz](https://markzware.com/products/pdfmarkz/) - Convert PDF content into InDesign/IDML, Affinity, and QuarkXPress.
- [Markzware QXPMarkz](https://markzware.com/qxpmarkz/) - Convert QuarkXPress documents to IDML, InDesign, and Affinity Publisher.
- [Markzware MarkzPortal](https://markzware.com/) - Cloud/SaaS service to preview, preflight, and convert InDesign, PDF, and QuarkXPress files to IDML and other formats in the browser.

## Database & Automated Publishing

- [EasyCatalog](https://www.65bit.com/software/easycatalog/) - The leading InDesign plug-in for database/catalog publishing (65bit Software). Merges product data from Excel, CSV, XML, databases, or PIM systems into templates; integrates with WoodWing and PIM platforms.
- [priint:suite](https://www.priint.com/en/solutions/database-publishing) - Enterprise database-publishing platform (WERK II) for InDesign, Illustrator, and Adobe Express, on desktop and server, automating catalogs, data sheets, and technical documentation.
- [WoodWing Studio](https://www.woodwing.com/) - Multichannel editorial and content-production system with InDesign integration and EasyCatalog support for automated catalog production.
- [4ALLPORTAL](https://4allportal.com/print-and-publish-automation) - DAM/PIM platform with print-and-publish automation via EasyCatalog, priint:suite, and CHILI publish.

## Creative Automation & Web-to-Print

- [CHILI publish](https://www.chili-publish.com/) - Online document editor and smart-template engine for brand-compliant creative automation, web-to-print, and self-service design.
- [IMG.LY CE.SDK](https://img.ly/products/creative-sdk) - A browser/native creative-editing SDK with an open-source [IDML importer](https://github.com/imgly/idml-importer) for bringing InDesign layouts into web apps.

## Localization & Translation

IDML is the de facto interchange format for translating InDesign documents, because translation tools can extract text while preserving layout, styles, and threading, then round-trip the result back to a print-ready file.

- [Redokun](https://redokun.com/) - A TMS specialized in InDesign/IDML translation, with in-context page previews, translation memory, and a companion InDesign plug-in that enriches IDML metadata.
- [Trados Studio](https://www.trados.com/) - The industry-standard CAT tool (RWS) with strong IDML file-type support and in-app InDesign preview.
- [Transl8ly](https://transl8ly.com/) - Browser-based IDML translation tool that previews a sample and returns translated IDML files while preserving document structure.
- [memoQ](https://www.memoq.com/) - CAT/TMS with detailed IDML (and ICML) import settings, including control over master-page stories and special characters.
- [Phrase](https://phrase.com/) - AI-powered localization platform supporting IDML in its translation workflows.
- [Crowdin](https://store.crowdin.com/idml) - Localization platform with native IDML support and configurable segmentation.
- [Smartling](https://help.smartling.com/hc/en-us/articles/360008144433-Adobe-InDesign-Files-IDML) - Translation management supporting both `.idml` and native `.indd`, plus an InDesign plug-in.
- [Lokalise](https://docs.lokalise.com/en/articles/6096267-indesign-idml) - TMS with IDML import for translating brochures, magazines, and books.
- [Smartcat](https://www.smartcat.com/idml-translator/) - AI translation platform with a layout-preserving IDML translation agent.
- [Transifex](https://www.transifex.com/) - Cloud localization platform with IDML support.
- [OmegaT](https://omegat.org/) - Free, open-source translation-memory tool (Java) that handles IDML files.

## Scripting & Automation

- [adobe-indesign-script-collection](https://github.com/dl6nm/adobe-indesign-script-collection) - ExtendScript scripts for automating InDesign tasks, including batch INDD → IDML export.
- [GeneratePackageSchema.jsx / GenerateSchema.jsx](https://community.adobe.com/t5/indesign-discussions/looking-for-icml-schema/m-p/7201868) - SDK scripts (run via `app.generateIDMLSchema`) that emit the RELAX NG schema matching your specific InDesign plug-in configuration.

## Related Formats

IDML has several siblings that share its XML model. Tooling for one is often reusable for the others.

- **ICML** - InCopy Markup; an IDML-based standalone XML file for a single InCopy story (used in editorial workflows). A subset of the IDML specification.
- **ICMA** - InCopy assignment file; the IDML-based assignment container.
- **IDMS** - InDesign Snippet; an IDML-based fragment representing a reusable set of page objects.
- **INX** - InDesign Interchange (the legacy XML format that IDML replaced as of InDesign CS5).
- **INDD** - The native binary InDesign document format. Not human-readable; typically converted to IDML for interchange.

## Books

- [XML and InDesign](https://www.oreilly.com/library/view/xml-and-indesign/9781449344153/) - Dorothy J. Hoskins' O'Reilly book on round-tripping structured content through InDesign, covering XML import, tagging, and IDML export for downstream publishing workflows (O'Reilly, 2013).
- [XML Publishing with Adobe InDesign](https://www.oreilly.com/library/view/xml-publishing-with/9781449397234/) - Dorothy J. Hoskins' compact guide to XML workflows in InDesign, including a walkthrough of the IDML and ICML package formats (O'Reilly, 2010).
- [InDesign automatisieren](https://dpunkt.de/produkt/indesign-automatisieren/) - Gregor Fellenz's reference on InDesign automation with GREP, JavaScript, and XML workflows, written by the author of the transpect idml2xml toolchain (dpunkt.verlag, 2015, German).

## Articles & Tutorials

- [What is IDML? (Markzware)](https://markzware.com/idmarkz/what-is-idml-whats-idml-file-adobe-indesign-markup-language/) - Plain-language explainer on the format and its uses.
- [How to translate InDesign files](https://redokun.com/blog/indesign-translation-plugin) - Practical walkthrough of the IDML-based localization workflow.
- [Efficient translation of InDesign IDML files](https://medical-language-service.com/en/efficient-translation-of-indesign-idml-files-how-to-make-your-multilingual-brochure-a-success/) - Why IDML is the right interchange point for multilingual layout work.
- [Parsing/extracting info from InDesign via API or SDK](https://community.adobe.com/t5/indesign-discussions/parsing-extracting-info-from-indesign-via-api-or-sdk/m-p/12361016) - Adobe community discussion on the realities (and limits) of reverse-engineering IDML without InDesign Server.
- [Batch Change Hyperlinks Across a Whole InDesign Document](https://creativepro.com/batch-change-hyperlinks-across-a-whole-indesign-document/) - David Blatner's classic recipe for mass-editing hyperlinks (and making other sweeping changes) by exporting to IDML and using find-and-replace on the XML.
- [Sleuthing With Snippets](https://creativepro.com/sleuthing-secrets-with-snippets/) - Mike Rankin uses InDesign's IDML-based Snippets feature as a detective tool to identify mysterious objects and characters in a document.
- [Harnessing the Power of Text Variables and IDML](https://creativepro.com/harnessing-the-power-of-text-variables-and-idml/) - Jeff Potter's in-depth case study on automating newspaper production with text variables and IDML templates (CreativePro members-only).

## Contributing

Contributions are welcome! Please read the [contribution guidelines](https://github.com/sindresorhus/awesome/blob/main/contributing.md) first, then open a pull request. Keep entries alphabetical within each section where practical, write descriptions as a single sentence starting with a capital and ending with a period, and only add projects that are genuinely useful and actively relevant to the IDML ecosystem.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the authors have waived all copyright and related or neighboring rights to this work.
