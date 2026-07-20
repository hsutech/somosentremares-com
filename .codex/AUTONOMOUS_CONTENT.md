# Autonomous SEO content publisher

This repository is one website in a larger portfolio. Work only on this repository and its domain.

## Source of truth

- Read `.codex/content-plan.xlsx` completely before acting.
- Use the workbook's domain, company, market, language, SERP target, keywords, priority and internal-link context.
- Never use another portfolio company, domain, address, keyword list or brand.
- Keep machine state in `.codex/content-state.json`. Create it if absent.

## Unattended run contract

Each scheduled run must process exactly one article from start to finish. Do not ask for routine approval.

1. Reconcile the previous run. If a previously pushed article is not live, diagnose and repair it before selecting another topic.
2. Read the workbook and state file.
3. Select the first unprocessed keyword by workbook order, preferring High, then Medium, then Low priority.
4. Check the repository and live site for duplicate intent, duplicate slug and cannibalization. If the keyword is unsuitable, record it as `skipped` with a reason and select the next eligible keyword in the same run.
5. Research the current top organic results in the correct country and language. Record concise source URLs and observations in the state file. Never invent SERP data.
6. Decide the article structure from the SERP: target at least 1,300 words and normally 1,800-2,400 words when competitors justify it.
7. Write the complete article in the domain's required language and follow the repository's existing page, blog, metadata, structured-data and design patterns.
8. Include, where genuinely relevant:
   - one unique H1, SEO title and meta description;
   - table of contents for long articles;
   - comparison table for listicles;
   - 3-4 real internal links already present on this domain;
   - 3-4 authoritative external sources;
   - 4-6 FAQs;
   - a discreet, factual company mention;
   - a soft contextual CTA;
   - a relevant YouTube embed only when it materially improves the article.
9. Use `$imagegen` to create a relevant, original featured bitmap image. Save it inside the repository's existing asset structure, optimize it for the web, use a descriptive filename and add meaningful alt text. Do not generate text-heavy imagery or fake product photography.
10. Update every required discovery surface used by this repository, including the blog index, sitemap, RSS/feed, related-content blocks or navigation when present.
11. Run the repository's documented checks. At minimum run the production build when one exists. Fix failures caused by this article. Do not alter or revert unrelated user changes.
12. Inspect the generated page at desktop and mobile widths when local preview tooling is available. Check text overflow, image loading, links, metadata and structured data.
13. Commit only files belonging to this article and the content-state update. Use a descriptive commit message and push to the deployment branch already configured by the repository.
14. Verify that the Cloudflare deployment completes and that the final custom-domain URL returns the new article correctly. If deployment verification is temporarily unavailable, record `pushed_unverified` and reconcile it at the start of the next run.
15. Update `.codex/content-state.json` with keyword, slug, publication date, final URL, commit SHA, sources and final status.

## Editorial safeguards

- Do not fabricate reviews, first-hand testing, authors, quotes, statistics, products, prices, ratings or local reputation.
- Do not call the company or any option "the best" without a transparent comparison method.
- Cite primary and authoritative sources for medical, legal, financial, regulatory or safety claims.
- For lending and finance websites, use neutral educational language, explain costs and eligibility carefully, include an appropriate disclaimer, and never imply guaranteed approval or guaranteed outcomes.
- Do not copy competitor text or closely reproduce competitor structure or wording.
- Do not publish thin pages merely to satisfy the schedule.

## Failure policy

- Continue automatically through recoverable research, writing, formatting and build issues.
- Stop the run without pushing if credentials are missing, the repository is on the wrong branch, there are conflicting user changes in files that must be edited, the build cannot be repaired safely, or claims cannot be verified.
- Report only a concise success summary or the exact blocker. Do not ask the user to choose the next topic.
- Never delete existing content or rewrite unrelated pages to make an article fit.

## Completion condition

When all workbook topics are `published` or `skipped`, perform no further content changes. Report that the queue is complete.
