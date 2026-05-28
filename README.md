# Skill Security Assessment

A Claude Code skill that performs adversarial security assessments on other skills and plugins before installation.

## What It Does

This skill acts as a pre-installation security gate. When you encounter a new Claude Code skill or plugin, run this assessment to get a comprehensive report covering:

- **Static analysis** of all source files for dangerous patterns
- **Supply chain audit** of dependencies and install hooks
- **Prompt injection detection** for LLM exploitation attempts
- **Runtime behavior prediction** for network activity and data exfiltration
- **Permissions review** for least-privilege violations
- **Secrets exposure** analysis
- **Persistence and evasion** detection
- **CI/CD integrity** review

The output includes a risk-scored findings list and a clear **Safe To Install?** verdict.

## Installation

### From the Claude Code Plugin Marketplace

```
/install-plugin https://github.com/randy-schneiderman/skill-security-assessment
```

### Manual Installation

Clone this repo into your Claude Code plugins directory:

```bash
git clone https://github.com/randy-schneiderman/skill-security-assessment.git \
  ~/.claude/plugins/marketplaces/skill-security-assessment
```

## Usage

The skill activates automatically when you ask Claude Code to assess a skill's security:

```
Scan this skill for security issues: <path-or-url>
```

```
Is this plugin safe to install?
```

```
/skill-security-assessment
```

## Output Format

The assessment produces a structured report:

1. **Executive Summary** - Overall trustworthiness assessment
2. **Threat Model** - Who could exploit this and how
3. **Findings** - Detailed vulnerability list with severity ratings
4. **Attack Paths** - Step-by-step compromise scenarios
5. **Indicators of Malicious Intent** - Deceptive or suspicious patterns
6. **Supply Chain Risk Assessment** - Dependency and maintainer trust analysis
7. **Recommended Sandboxing** - Isolation recommendations
8. **Required Mitigations** - What must be fixed before installation
9. **Safe To Install?** - YES / NO / ONLY IN ISOLATED SANDBOX

## Philosophy

This skill assumes a hostile posture by default:

- The skill under review may be malicious
- The maintainer may be compromised
- Dependencies may contain implants
- Documentation may be misleading
- False positives are preferred over missed detections

## License

MIT - see [LICENSE](LICENSE) for details.
