---
description: Summarize web articles and save them to the central knowledge base with consistent formatting and metadata
---

Act as a research assistant and documentation specialist focused on creating high-quality article summaries for the central knowledge base.

**Note:** This workflow is for web articles and external resources. For repository documentation, use `/repo-content-summary` instead.

Must discuss with user each point, maintaining an easy, conversational tone.

## 1. **article-input**
- Collect the article URL from the user
- Verify the URL is accessible and valid
- **If YouTube URL detected** (youtube.com or youtu.be): Note that transcript extraction will be needed
- Ask for any specific focus areas or key points to emphasize
- Confirm the target filename (suggests `YYYYMMDDHHmm - Summary - {short 3-5 word topical title}.md` format)

## 2. **content-extraction**
// turbo
- **For standard articles**: Use read_url_content to fetch the article
- **For YouTube videos**: 
  - Attempt to get transcript from read_url_content first
  - If transcript not available via web scraping, check `.windsurf/skills/` for relevant transcript extraction skills
  - Follow the skill's guidance to extract and parse the transcript
- Analyze the content structure and identify main sections
- Extract key information: title, author, publication date, main concepts
- If content is fragmented, use view_content_chunk to get complete article

## 3. **summary-generation**
- Create a succinct summary following established patterns:
  - **Core Thesis**: 1-2 sentences capturing the main argument upfront
  - **Key Points**: Main findings organized with tables for comparisons
  - **Code Examples**: Limit to 1-2 illustrative blocks (not full implementations)
  - **Related Reading**: Capture links to resources referenced in the article
  - **Relevance**: Connect to specific existing files only (not generic folders)

## 4. **metadata-creation**
- Generate YAML frontmatter with:
  ```yaml
  ---
  title: "Article Title Summary"
  tags:
    - relevant-tag
    - another-tag
  source: "original-url"
  author: "Primary Author, Contributor 1, Contributor 2"
  dateCreated: YYYY-MM-DD
  ---
  ```
- Extract tags based on content topics and technologies
- Include cross-references to related project files when relevant

## 5. **file-creation**
// turbo
- Create the summary file in `0 📥 Capture/`
- Use naming convention `YYYYMMDDHHmm - Summary - {short 3-5 word topical title}.md`
- Ensure proper markdown formatting and structure
- Include source attribution and relevant internal links

## 6. **validation**
- Review the generated summary for completeness
- Verify all important concepts are captured
- Check formatting consistency with existing summaries
- Confirm file is saved in correct location with proper naming

## 6b. **self-review**
Before presenting to user, evaluate the draft against the source:
- What is missing from the article?
- What was added that isn't in the article?
- What could be simpler or more succinct?
- Are any sections redundant with each other?
- Do connections link to actual files or just generic folders?

Revise based on findings before proceeding.

## 7. **verify-connections**
- Search for relevant existing notes before creating connections:
  - Use find_by_name or grep_search to locate related project files
  - Check `01 - Projects/[Project]/` for project-specific documents
  - Check `02 - Documentation/` for technical documentation
  - Check `04 - Quick Notes/Tasks/` for related tasks
- Only create wiki-links to specific files that actually exist and are directly relevant
- **Never** link to generic folders (e.g., `[[04 - Quick Notes/Tasks/|Various tasks]]`)
- If grep_search returns no relevant matches, omit Connections section entirely

## 8. **integration**
- Link the summary to relevant project files or documents
- Add to any existing knowledge bases or documentation indices
- Consider creating cross-references in related files
- Update any tracking systems or dashboards if applicable

## Quality Standards

### **Content Requirements**
- [ ] Core thesis captured in 1-2 sentences at the top
- [ ] Clear, concise writing with proper technical terminology
- [ ] Logical organization with descriptive headings
- [ ] Proper attribution to original source (include all credited authors)

### **Brevity Standards**
- [ ] Code examples limited to 1-2 illustrative blocks (not full implementations)
- [ ] Prefer tables over nested bullet lists for comparisons
- [ ] Target 50-120 lines total (not counting frontmatter)
- [ ] Remove sections that duplicate information from other sections

### **Formatting Requirements**
- [ ] YAML frontmatter with all required fields
- [ ] Consistent markdown structure with existing summaries
- [ ] Proper code block formatting with language specification
- [ ] Bullet points for lists and key findings
- [ ] Internal links to related project files

### **Naming Convention**
- [ ] Format: `YYYYMMDDHHmm - Summary - {short 3-5 word topical title}.md`
- [ ] Use timestamp format YYYYMMDDHHmm (year, month, day, hour, minute)
- [ ] Include short 3-5 word topical title describing the content
- [ ] Use spaces and hyphens as shown in format

## Template Structure

```markdown
---
title: "Article Title Summary"
tags:
  - primary-topic
  - secondary-topic
  - technology
source: "https://example.com/article-url"
author: "Primary Author, Contributor 1, Contributor 2"
dateCreated: YYYY-MM-DD
---

# Summary: Article Title

*Source: [Author Name](https://example.com/article-url)*

## Core Thesis
[1-2 sentences capturing the article's main argument or takeaway]

## Key Points
[Organized findings - prefer tables for comparisons over nested lists]

## Technical Details
[1-2 illustrative code examples if applicable, not full implementations]

## Relevance to Work
[Connection to specific existing files - omit if no relevant matches found]

## Related Reading
[Links to articles/resources referenced in the source - omit if none]
```

## Integration Points

- **Related workflows**: `/day-prep` for daily research tasks, `/repo-content-summary` for repository docs
- **Output location**: `0 📥 Capture/` (inbox for processing)
- **Templates**: Reference existing summary files for formatting patterns
- **Cross-references**: Link to relevant files when found via search
- **Distinction**: Article summaries are vault-wide knowledge; repo summaries are project-specific

## Troubleshooting

- **URL Access Issues**: Try alternative URLs or check for paywalls
- **Content Fragmentation**: Use multiple view_content_chunk calls to get complete content
- **Naming Conflicts**: Add date or specific topic identifier to filename
- **Formatting Issues**: Reference existing summaries for consistent structure
