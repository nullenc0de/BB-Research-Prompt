# DomainHarvester

## What is DomainHarvester?

DomainHarvester is an advanced LLM prompt engineered to comprehensively map an organization's complete digital footprint, including all domains owned by a company, its acquisitions, subsidiaries, and parent entities. It creates a structured report that provides deep visibility into a target's entire domain portfolio, including often-overlooked or forgotten digital assets.

## Key Features

- **Complete Corporate Structure Mapping**: Identifies parent-subsidiary relationships
- **Acquisition Chain Discovery**: Maps domains from acquisitions of acquisitions
- **Historical Domain Tracking**: Finds domains from previous company names and brands
- **Comprehensive Domain Inventory**: Produces a clean, copy-pastable list of all discovered domains
- **Hierarchical Organization**: Structures domains according to corporate relationships
- **Active Status Verification**: Indicates which domains are active, redirected, or potentially abandoned

## Use Cases

- **Security Research**: Discover forgotten domains that may have weaker security
- **Bug Bounty Hunting**: Map your complete attack surface for vulnerability discovery
- **M&A Due Diligence**: Document digital assets before corporate acquisitions
- **Brand Protection**: Identify all properties requiring brand enforcement
- **Competitive Intelligence**: Understand a competitor's complete digital presence
- **Digital Asset Management**: Discover forgotten or unmaintained properties

## Using DomainHarvester

DomainHarvester is a prompt designed to work with advanced Large Language Models (LLMs) with web search capabilities.

### Requirements

- Access to an advanced LLM with web search capabilities (Claude, GPT-4, etc.)
- Basic understanding of corporate structures and web domains

### Instructions

1. Copy the entire prompt from below
2. Paste it into your conversation with the LLM
3. Replace `[COMPANY_NAME/DOMAIN]` with your target organization or domain
4. Submit and wait for the comprehensive report

### The Prompt

```
I need you to conduct comprehensive research on [COMPANY_NAME/DOMAIN] to map out its complete digital footprint, including all associated domains, acquisitions, and corporate relationships. Create a detailed report that organizes this information in a clear, hierarchical structure.

### PART 1: COMPANY OVERVIEW

1. COMPANY IDENTIFICATION
   - Identify the exact legal name of the company
   - Determine headquarters location and year founded
   - Map parent company relationships (if any)
   - Identify any holding companies or conglomerates that own the company
   - Document legal structure (public/private, incorporation details)
   - Link to official company website and primary domains

2. CORPORATE HISTORY TIMELINE
   - Create a chronological timeline of the company's major milestones
   - Document all name changes the company has undergone
   - Map significant restructuring events (mergers, splits, etc.)
   - Identify previous parent companies or ownership changes
   - Note any bankruptcy events or major reorganizations
   - Document geographical expansion history

### PART 2: ACQUISITIONS & SUBSIDIARIES MAPPING

3. DIRECT ACQUISITIONS
   - List all companies acquired directly by the target company
   - Document acquisition dates and transaction values when available
   - Include the status of each acquired company (fully integrated, operates independently, rebranded, shut down)
   - Identify the primary business function/purpose of each acquisition
   - Note whether the acquired brand name is still in use
   - Document any post-acquisition security incidents

4. SUBSIDIARIES & DIVISIONS
   - Identify all subsidiaries (both wholly and partially owned)
   - Document joint ventures and their ownership percentages
   - Map out divisions or business units with distinct branding
   - Identify international subsidiaries and their market focus
   - Document holding companies created for tax or legal purposes
   - Map operational relationships between different subsidiaries

5. RECURSIVE ACQUISITION CHAINS
   - Identify acquisitions made by the company's acquisitions ("acquisition chains")
   - Document the full organizational hierarchy depth
   - Map holding company structures that may obscure ownership
   - Identify companies that were acquired multiple times
   - Document restructuring of acquisitions after purchase
   - Track renamed or rebranded acquisitions that may be difficult to identify

### PART 3: DOMAIN & DIGITAL ASSET DISCOVERY

6. PRIMARY DOMAINS
   - List all primary domains used by the main company
   - Document TLD variations (.com, .org, .net, country-specific TLDs)
   - Identify domains used for different company functions (corporate, marketing, support)
   - Document historical domains that may still be in use
   - Map email domain patterns
   - Identify domains used for internal company systems

7. SUBSIDIARY & ACQUISITION DOMAINS
   - Map all domains associated with subsidiaries and acquisitions
   - Document whether original acquisition domains are still active or redirected
   - Identify country-specific domains for international operations
   - Map product-specific domains that may be separate from main company domains
   - Document internal/employee domains related to subsidiaries
   - Identify historical domains from acquired companies that may still be active

8. SUBDOMAINS & DIGITAL INFRASTRUCTURE
   - Identify significant subdomains for main company and acquisitions
   - Document development, staging, and testing environments
   - Map cloud infrastructure naming patterns (AWS S3, Azure, GCP)
   - Identify API domains and service endpoints
   - Document content delivery networks and their domains
   - Map authentication and identity management domains

9. DIGITAL MARKETING FOOTPRINT
   - Identify domains used for marketing campaigns
   - Document landing page and microsites
   - Map domains for affiliate programs or partner portals
   - Identify contest, promotion, or temporary campaign domains
   - Document domains for specific product lines or brands
   - Map domains used for different geographical markets

10. TECHNOLOGY SERVICES & PLATFORMS
    - Identify domains for SaaS or technology products offered by the company
    - Document customer portals and service access points
    - Map mobile app backend services and API domains
    - Identify developer portals and documentation sites
    - Document domains for specific technology stacks or platforms
    - Map domains for technology showcases or demos

### PART 4: CORPORATE RELATIONSHIP ANALYSIS

11. INVESTMENT & PARTNERSHIP MAPPING
    - Document significant corporate investments made by the company
    - Identify strategic partnerships and their digital presence
    - Map joint ventures and their associated domains
    - Document technology licensing relationships
    - Identify white-label service providers or customers
    - Map industry consortiums or associations led by the company

12. BRAND PORTFOLIO ANALYSIS
    - Document all brands owned by the company and its acquisitions
    - Map product lines that have their own digital presence
    - Identify co-branded initiatives with other companies
    - Document brand evolution through acquisitions
    - Map regional variations of brands and their domains
    - Identify discontinued brands that may still have online presence

### PART 5: REPORT COMPILATION

13. DOMAIN HIERARCHY VISUALIZATION
    - Create a hierarchical tree of all company domains, subdomains, and acquired domains
    - Group domains by corporate structure and relationship
    - Distinguish between active, redirected, and potentially abandoned domains
    - Indicate hosting relationships where identifiable
    - Mark domains with potential security significance (e.g., legacy systems, obsolete platforms)
    - Highlight domains that appear to have different security practices

14. ACQUISITION TIMELINE VISUALIZATION
    - Create a chronological timeline of all acquisitions
    - Map relationship between acquisitions and domain changes
    - Indicate when acquired companies were renamed or rebranded
    - Document when acquired domains were migrated or consolidated
    - Highlight acquisition clusters (periods of high acquisition activity)
    - Map technology migrations following acquisitions

15. DATA SOURCE DOCUMENTATION
    - List all sources used in research (SEC filings, press releases, etc.)
    - Document search methodologies used to discover domains
    - Note any conflicting information found during research
    - Indicate confidence level for different information points
    - Document limitations in the research process
    - Identify areas where additional research may be valuable

16. COMPREHENSIVE DOMAIN LIST
    - Create a complete, plain-text list of all identified domains and subdomains
    - Format the list for easy copy-paste operations
    - Organize in a clear, structured manner (primary domains, subdomains, acquisition domains)
    - Include status indicators (active, redirected, potentially inactive)
    - Add brief notes for domains with special significance
    - Ensure every domain discovered in the research is included in this master list

### FINAL INSTRUCTIONS

- Focus only on publicly available information
- Prioritize authoritative sources (SEC filings, company press releases, official announcements)
- Indicate clearly when information is based on inference rather than explicit confirmation
- Structure information hierarchically to show corporate relationships clearly
- Create tables or lists that are easy to scan for domain information
- Highlight particularly significant findings or unusual patterns
- Include URLs to source materials where possible
- End the report with a comprehensive, plain-text list of ALL discovered domains for easy copy-paste
- Format the final domain list by category (primary, subsidiary, acquisition, etc.) with no additional text or explanation
- Include both active and historical domains in the final list, with simple status indicators

Produce this comprehensive digital footprint report for [COMPANY_NAME/DOMAIN], focusing on creating a complete map of domains, subdomains, and digital assets across the entire corporate structure, including all acquisitions and subsidiaries.
```

## Example Output

The output will be a detailed report containing:

1. **Company Overview**: Legal structure and corporate relationships
2. **Acquisition Map**: Complete hierarchy of all acquired companies
3. **Domain Inventory**: Exhaustive list of all domains and subdomains
4. **Corporate Relationship Analysis**: Investments, partnerships, joint ventures
5. **Domain List**: A clean, copy-pastable list of all discovered domains

Here's a small sample of what the domain list output might look like:

```
# PRIMARY DOMAINS (ACTIVE)
example.com
example.net
example.org

# SUBSIDIARY DOMAINS (ACTIVE)
subsidiary1.com
subsidiary2.co.uk

# ACQUISITION DOMAINS (ACTIVE)
acquisition1.com
acquisition2.io

# HISTORICAL DOMAINS (INACTIVE/REDIRECTED)
old-example.com (redirects to example.com)
legacy-brand.net (potentially inactive)
```

## Tips for Better Results

- Be as specific as possible about the target company
- For large conglomerates, consider focusing on specific divisions initially
- Follow up with specific queries about interesting acquisitions
- Request deeper analysis of particular subsidiaries when needed
- Run the prompt with different variations of the company name for maximum coverage

## Contributing

We welcome contributions to improve the DomainHarvester prompt:

1. Fork the repository
2. Make your changes
3. Submit a pull request with a clear description of your improvements

## Ethical Usage

This tool is designed for legitimate business and security purposes only. Always:

- Respect privacy and terms of service of websites
- Only collect publicly available information
- Use findings responsibly and ethically
- Obtain proper authorization before security testing
- Follow responsible disclosure practices for any vulnerabilities discovered

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This tool is provided for educational and ethical security research purposes only. The creators are not responsible for misuse or any damages resulting from the use of this tool. Always ensure you have proper authorization before conducting security testing against any systems.
