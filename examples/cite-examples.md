# Citation Format Examples

## ✅ RECOGNIZED FORMATS

### Direct Citations (single author)
1. `@smith` → `\citeauthor{smith} (\citeyear[]{smith})`
2. `@smith [p. 123]` → `\citeauthor{smith} (\citeyear[p.~123]{smith})`
3. `@smith [pp. 45-67]` → `\citeauthor{smith} (\citeyear[pp.~45-67]{smith})`
4. `@smith [pp. 10, 15, 20]` → Direct citations with commas in page numbers work

### Indirect Citations (multiple authors)
5. `[@smith]` → `(\citeauthor{smith} \citeyear[]{smith})`
6. `[@smith, p. 123]` → `(\citeauthor{smith} \citeyear[p.~123]{smith})`
7. `[@smith; @jones]` → `(\citeauthor{smith} \citeyear[]{smith}; \citeauthor{jones} \citeyear[]{jones})`
8. `[@smith, p. 123; @jones, pp. 45-67]` → Citations with page numbers
9. `[@smith, pp. 10, 15, 20]` → Single author with commas in page numbers
10. `[see @smith]` → Simple text before single citation
11. `[@smith; @jones; @brown]` → Three or more authors work

### Complex indirect citations (now supported!)
12. `[for more info, see @smith, pp. 10, 15; @jones, ch. 2, 5]` → **NOW WORKS**: Complex prefatory text with multiple authors and comma-separated pages
13. `[see @smith, pp. 1, 3, 5; @jones]` → **NOW WORKS**: Mixed citations with and without pages
14. `[cf. @smith, p. 123; also @jones, pp. 10, 15]` → **NOW WORKS**: Complex prefatory text distributed throughout
15. `[for background, see @smith, pp. 1, 3; @jones, ch. 2; @brown, pp. 45, 67]` → **NOW WORKS**: Three authors with mixed page formats

### Author name formats
16. `@smith-jones` → Authors with hyphens work
17. `@smith2023` → Authors with numbers work  
18. `@abc-def2024xyz` → Complex author names work

## ❌ STILL NOT RECOGNIZED FORMATS

### Invalid author formats
- `@Smith` (uppercase not allowed)
- `@123smith` (cannot start with number)
- `@smith_jones` (underscore not allowed)
- `@smith.jones` (period not allowed)

### Invalid bracket formats
- `[@smith` (missing closing bracket)
- `@smith]` (missing opening bracket)
- `[[@smith]]` (double brackets)

### Invalid separators
- `[@smith, @jones]` (comma instead of semicolon between authors)
- `[@smith | @jones]` (pipe separator not supported)

### Nested brackets
- `[@smith [see also @jones]]` (nested citations not supported)

## 🔧 HOW THE NEW PARSING WORKS

The improved parser:
1. **Identifies all authors first** using regex to find their positions
2. **Processes each author segment** to look for page information
3. **Distinguishes comma types** - only commas immediately after @author are treated as page separators
4. **Preserves prefatory text** by not splitting on commas in descriptive text

This solves the fundamental limitation where prefatory commas were confused with page-separating commas.
