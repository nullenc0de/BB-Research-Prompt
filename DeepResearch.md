# BB-Research-Prompt: Advanced Target Research & Vulnerability Discovery Prompt

## Overview

BugBountyGPT is an advanced LLM prompt designed to transform bug bounty hunting through AI-assisted research. This tool helps security researchers identify high-impact, reportable vulnerabilities in target organizations using only publicly available information, focusing on issues likely to qualify for bug bounty rewards.

### Key Features

- **Comprehensive Target Analysis**: Deep dive into a company's public footprint
- **Acquisition-Focused Research**: Special emphasis on security risks in acquired companies
- **Historical Vulnerability Mapping**: Analysis of past incidents to predict future weaknesses
- **Industry-Specific Vulnerability Patterns**: Tailored approaches for different sectors
- **Practical Exploitation Guidance**: Clear validation steps for each potential vulnerability

## Prerequisites

- Access to a capable large language model with web search capabilities (Claude, GPT-4, or similar)
- Basic understanding of security concepts and bug bounty programs
- Commitment to ethical, responsible security research

## How To Use

1. **Copy the Prompt**: Use the full prompt provided below
2. **Insert Target Company**: Replace `[COMPANY NAME]` with your target organization
3. **Submit to LLM**: Use any advanced LLM with web search capabilities 
4. **Review the Output**: Carefully analyze the generated report
5. **Validate Findings**: Test identified vulnerabilities within program scope
6. **Submit Reports**: Create proper bug reports based on validated findings

## The Master Prompt

```
I need you to research [COMPANY NAME] with the specific goal of uncovering reportable security vulnerabilities for bug bounty submission. Create a focused report that identifies high-impact security issues using only publicly available information. Each finding should be detailed enough to guide initial testing and validation, prioritizing issues likely to qualify for bounty rewards. Include industry-specific vulnerabilities relevant to [COMPANY NAME]'s business model and technology stack.

### INTRODUCTION
- Brief company overview and business model
- Core technologies and platforms used
- Industry-specific security considerations
- Bug bounty program details (if available)
- Key dates and methodology of research
- Comprehensive acquisition history with timeline
- Overview of significant partnerships and integrations

### PART 1: TARGETED ASSET DISCOVERY

1. HIGH-VALUE ASSET IDENTIFICATION
   - Map domains, subdomains, and IP ranges with focus on non-production environments (test/staging/dev)
   - Identify forgotten/abandoned assets (orphaned subdomains, decommissioned services, test environments)
   - Search for leaked cloud resources (S3 buckets, Azure storage, GCP resources) with specific naming patterns
   - Flag assets that appear outside typical security controls or monitoring
   - Identify subdomain takeover opportunities (dangling CNAME/DNS records pointing to abandoned cloud resources)
   - Check archived pages (Wayback Machine) for references to legacy systems or endpoints

2. VULNERABILITY-FOCUSED TECH STACK ANALYSIS
   - Identify frameworks, libraries, and components with recent CVEs or security advisories
   - Detect outdated dependencies through version fingerprinting in public-facing assets
   - Map cloud services that commonly have misconfiguration issues (Lambda, S3, Azure Functions)
   - Document CDN implementations with potential for cache poisoning or bypass
   - Flag any technology components with known security weaknesses, especially those recently disclosed
   - List specific version numbers where possible (e.g., "React <18.2.0 with CVE-2022-XXXXX")
   - Cross-reference technologies with the OWASP Top 10 for corresponding vulnerability types

3. API VULNERABILITY HOTSPOTS
   - Discover undocumented or internal APIs accidentally exposed to the public
   - Extract API endpoints from client-side JavaScript code and browser network requests
   - Identify APIs with weak authentication/authorization patterns (JWT issues, token validation)
   - Find API endpoints with potential IDOR vulnerabilities by manipulating IDs (sequential, UUIDs, etc.)
   - Detect GraphQL endpoints and assess for introspection/query depth issues
   - Document APIs handling sensitive operations (financial transactions, PII) that might lack rate limiting
   - Locate examples of API requests in client-side code that reveal parameter structures for fuzzing
   - Check for versioned APIs that may have legacy endpoints still accessible with weaker security

4. THIRD-PARTY INTEGRATION & ACQUISITION WEAK POINTS
   - Identify third-party scripts with potential for XSS or supply chain attacks
   - Map payment processors, SSO providers, and other security-critical integrations
   - Look for public OAuth implementations with potential redirect or scope vulnerabilities
   - Detect shadow IT tools mentioned by employees that might connect to company data
   - Document public webhooks, callbacks, or data exchange endpoints between systems
   - Create a comprehensive list of all company acquisitions from press releases and financial filings
   - Identify all domains, subdomains, and digital assets associated with acquired companies
   - Analyze integration points between parent company and acquisitions for security gaps
   - Check for abandoned or poorly maintained assets from acquired companies
   - Investigate whether acquired technology stacks differ from parent company standards
   - Review post-acquisition security incidents that might reveal systemic integration issues
   - Document transition timelines for integrating acquired systems to identify security gaps
   - Analyze SEC filings for disclosures about security incidents involving acquired companies
   - Map authentication systems across acquisitions to identify inconsistent security controls
   - Research known vulnerabilities specific to acquired companies' technology stacks

5. CREDENTIAL AND SENSITIVE DATA EXPOSURE
   - Search public repositories for leaked API keys, tokens, or hardcoded credentials
   - Identify authentication bypass opportunities in publicly visible systems
   - Look for exposed internal documents, configuration files, or backup data
   - Find employee screenshots showing internal URLs, dashboards, or system names
   - Detect development artifacts with database connection strings or environment variables
   - Identify public Trello boards, Slack channels, or collaboration tools with company data

### PART 2: REPORTABLE VULNERABILITY DISCOVERY

6. SERVERLESS AND CLOUD FUNCTION VULNERABILITIES
   - Identify exposed Lambda functions, Azure Functions, or Cloud Run services
   - Look for cloud storage (S3, Blob Storage, GCS) with weak access controls
   - Detect IAM misconfigurations or overly permissive policies in public resources
   - Search for leaked cloud credentials or configuration files in public repositories
   - Identify containerized applications with potentially exposed management interfaces

7. AUTHENTICATION AND SESSION VULNERABILITIES
   - Identify single sign-on (SSO) implementations with potential for account takeover
   - Map password reset flows with logic flaws or weak validation
   - Document JWT usage patterns and potential signature verification bypasses (weak algorithms, missing checks)
   - Look for cookie attributes missing secure/httpOnly flags or weak session management
   - Find multi-factor authentication bypass opportunities or implementation flaws
   - Detect OAuth flows with redirect_uri validation issues or token leakage risks
   - Check for signature replay attacks in crypto wallet authentications
   - Test for token expiration issues or insufficient token validation

8. BUSINESS LOGIC AND ACCESS CONTROL FLAWS
   - Identify potential IDOR (Insecure Direct Object Reference) vulnerabilities in APIs or endpoints
   - Map multi-step processes (checkout, account management) with potential state manipulation flaws
   - Look for race conditions in critical transactions or data processing
   - Document authorization check bypasses or privilege escalation paths
   - Detect inconsistent security controls across related features or endpoints
   - Find parameter pollution or HTTP method switching opportunities

9. CLIENT-SIDE AND FRONTEND VULNERABILITIES
   - Identify DOM-based XSS opportunities in JavaScript frameworks
   - Document CSP (Content Security Policy) bypass potential
   - Look for sensitive data exposed in client-side storage (localStorage, IndexedDB)
   - Find client-side validation that could be bypassed for server-side attacks
   - Detect insecure postMessage implementations or cross-origin vulnerabilities
   - Check for browser extension integrations with weak messaging security

10. EMERGING TECHNOLOGY ATTACK SURFACES
    - Identify AI/ML systems with potential for prompt injection or data poisoning
    - Find mobile app deep linking vulnerabilities or custom URL scheme abuse opportunities
    - Map WebSocket connections with authentication/authorization weaknesses
    - Detect GraphQL endpoints with introspection enabled or query depth issues
    - Look for webhooks with weak validation or replay vulnerabilities
    - Identify new or experimental features mentioned in release notes or documentation

### PART 3: EXPLOITATION AND REPORTING GUIDANCE

11. VULNERABILITY VALIDATION PATHS
    - Provide specific testing methodologies for each identified vulnerability
    - Include exact curl commands, HTTP requests, or browser console code for validation
    - Document parameters to fuzz or manipulate for triggering the issue
    - Suggest tools or scripts useful for exploitation of discovered weaknesses
    - Outline multi-step attack chains that increase impact severity
    - Provide specific examples of payloads for different vulnerability types
    - Include real endpoint URLs based on the discovered assets
    - Map vulnerability validation techniques specific to acquired company assets
    - Document potential cross-domain or cross-origin testing between parent and acquired entities
    - Highlight differences in validation approaches needed for different technology stacks

12. BOUNTY MAXIMIZATION STRATEGIES
    - Categorize findings by potential payout tiers based on similar programs
    - Suggest impact demonstrations that elevate severity ratings
    - Identify business context that increases the perceived risk
    - Document affected user populations or data types to demonstrate scope
    - Provide report templates tailored to the company's security team expectations
    - Flag vulnerabilities that might qualify for special bonuses (remote code execution, account takeover)

13. CHAIN-EXPLOITATION OPPORTUNITIES
    - Identify how vulnerabilities could be chained together for greater impact
    - Map potential privilege escalation paths across different systems
    - Document how initial access could lead to lateral movement
    - Suggest ways to pivot from lower-severity to higher-severity findings
    - Show how multiple medium-risk issues might combine into critical-risk scenarios
    - Analyze potential exploit chains that cross between parent company and acquisition assets
    - Identify trust relationships between domains that could enable pivoting between systems
    - Document authentication and authorization boundaries that might be bypassed between integrated systems
    - Map data flow between acquired assets and parent systems for potential exfiltration paths

### PART 4: REPORT STRUCTURING

14. PRIORITY FINDINGS SUMMARY
    - List of the most promising bug bounty opportunities ranked by potential payout
    - Risk summary with CVSS scores for each critical finding
    - Quick-win vulnerabilities that can be rapidly validated
    - Novel or unique vulnerabilities likely to attract attention
    - Time-sensitive issues that should be prioritized (e.g., new CVEs, exposed credentials)

15. DETAILED VULNERABILITY REPORTS
    - Technical write-up for each vulnerability following standard bug bounty report formats
    - Affected assets, endpoints, or components with specific URLs or identifiers
    - Clear reproduction steps with exact HTTP requests and responses
    - Visual evidence placeholders (where screenshots would be added after validation)
    - Impact description focusing on business risk and security implications
    - Suggested PoC code or commands with actual values (URLs, parameters, payloads)
    - CVSS score calculation with justification for each vulnerability

16. TESTING METHODOLOGY & TOOLS
    - Specific approaches for validating each finding
    - Recommended tools for exploitation and verification
    - Safe testing guidelines to avoid service disruption
    - Browser extensions, burp plugins, or scripts useful for testing
    - Time estimates for validation of each vulnerability type

17. BUG BOUNTY PROGRAM CONTEXT
    - Analysis of the company's bug bounty program structure and rules
    - Historical payout patterns and preferred vulnerability types
    - Out-of-scope items to avoid wasting time on
    - Special bonuses or incentives currently offered
    - Communication tips for this specific security team based on public interactions
    - Similar vulnerabilities previously reported to guide unique findings

18. INDUSTRY-SPECIFIC VULNERABILITY PATTERNS
    - Identify vulnerabilities specific to the company's industry or business model
    - For blockchain/NFT companies: 
        * Smart contract vulnerabilities (reentrancy, front-running, integer overflow)
        * Wallet signature replay attacks
        * NFT metadata manipulation
        * Gas limit exploitation
        * Oracle manipulation risks
    - For fintech: 
        * Payment flow manipulation
        * Financial logic flaws
        * Banking API integration weaknesses
        * Regulatory compliance gaps (PCI-DSS)
    - For healthcare: 
        * PHI exposure risks
        * Patient data access controls
        * Medical device API vulnerabilities
        * HIPAA compliance issues
    - For e-commerce: 
        * Cart/checkout manipulation
        * Pricing errors
        * Discount/coupon abuse
        * Inventory race conditions
    - For SaaS: 
        * Tenant isolation bypasses
        * Subscription enforcement flaws
        * API key management issues
        * Data segregation problems
    - Provide industry-specific test cases relevant to the company's core functions
    - Include references to similar vulnerabilities found in competitors or related companies

19. HISTORICAL VULNERABILITIES AND INCIDENTS
    - Research past security incidents affecting the company
    - Document previously disclosed vulnerabilities in public bug bounty programs
    - Analyze breach reports and security researcher write-ups about the company
    - Identify patterns in the types of vulnerabilities historically affecting the company
    - Look for vulnerabilities that may have been incompletely patched
    - Reference similar vulnerabilities found in competitors in the same industry
    - Map security incidents to current assets and systems that might still be vulnerable
    - Review SEC filings for security incident disclosures, especially following mergers and acquisitions
    - Analyze regulatory enforcement actions related to security incidents
    - Examine historical credential stuffing attacks targeting the company or industry
    - Document ransomware incidents affecting the company or its acquisitions
    - Investigate past data breaches and the company's disclosure and remediation efforts
    - Research customer complaints about account security on social media platforms
    - Analyze timing patterns of past incidents (e.g., proximity to major product launches)

20. KEY CITATIONS AND REFERENCES
    - List all sources referenced in the report
    - Include links to official documentation
    - Reference relevant CVEs and security advisories
    - Link to bug bounty program details
    - Cite any technical articles or research papers mentioned
    - Include Etherscan links or blockchain explorers for smart contract references
    - Reference applicable OWASP guides or CWE entries for vulnerability categories

### FINAL INSTRUCTIONS

- Focus only on publicly available information - NO active scanning or testing
- Prioritize findings by bounty potential, technical impact, and uniqueness
- Ensure each vulnerability includes clear validation steps for confirmation
- Include specific curl commands, request samples, or browser console code where relevant
- Distinguish between confirmed vulnerabilities and potential issues requiring validation
- Highlight novel or creative findings that demonstrate researcher skill
- Format vulnerability reports in the style preferred by major bug bounty platforms
- Focus on actionable, high-value issues rather than minor findings
- Include references to CVEs, CWEs, or similar vulnerabilities for context
- Structure findings to demonstrate clear security impact, not just technical flaws
- Use language that reflects confidence levels in findings (e.g., "strongly suggests," "evidence indicates," "appears to have")
- Balance technical depth with readability for security teams
- Ensure all findings are ethically discoverable through passive means

Generate this bug bounty hunting guide for [COMPANY NAME], focusing exclusively on reportable vulnerabilities with clear reproduction steps and bounty potential.
```

## Example Report Structure

The output should follow this general structure:

1. **Target Company Profile** - Business overview and technical context
2. **Key Security Risks** - High-level analysis of most critical vulnerability vectors
3. **Asset Inventory** - Comprehensive mapping of attack surface
4. **Vulnerability Analysis** - Detailed breakdown of security issues
5. **Validation & Exploitation Guidance** - Step-by-step testing instructions
6. **Reporting Templates** - Bug report formats for submission

## Benefits of Using BugBountyGPT

- **Saves Extensive Research Time**: Automates the collection and correlation of target information
- **Identifies Non-Obvious Attack Vectors**: Often reveals security issues other researchers miss
- **Adapts to Different Industries**: Tailors vulnerability hunting to specific business sectors
- **Highlights Acquisition Risks**: Focuses on often-overlooked integration security issues
- **Optimizes for Reward Potential**: Prioritizes findings by likely bounty payout

## Legal and Ethical Use

This tool is designed for:
- Legitimate bug bounty hunting within program scope
- Responsible security research following disclosure guidelines
- Ethical hacking with proper authorization

Always follow these principles:
- Only test within authorized scope and boundaries
- Report vulnerabilities through proper channels
- Respect program rules and disclosure timelines
- Do not access, modify, or exfiltrate sensitive data
- Minimize impact on production systems during testing

Remember that this prompt only identifies potential issues based on public information. Always validate findings and follow responsible disclosure practices.

## Contributing

Contributions to improve the prompt or extend its capabilities are welcome. Please submit a pull request with your suggested changes.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Inspired by countless bug bounty reports and security researcher techniques
- Special thanks to the bug bounty and responsible disclosure community

## Disclaimer

This tool is provided for educational and ethical security research purposes only. The creators are not responsible for misuse or any damages resulting from the use of this tool. Always ensure you have proper authorization before conducting security testing against any systems.
