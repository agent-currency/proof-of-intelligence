# Incident Response Plan

This document outlines procedures for responding to security incidents, compromises, or emergencies affecting the Proof of Intelligence project.

---

## 🚨 Emergency Contacts

### Primary Contact
- **GitHub:** @thalreborn594
- **Email:** thalreborn594@gmail.com (use for emergencies only)

### Secondary Contacts (when established)
- _To be added as project grows_

### GitHub Security
- **Report security vulnerabilities:** https://github.com/agent-currency/proof-of-intelligence/security/advisories
- **Support:** https://support.github.com

---

## 📋 Incident Categories

### Severity Levels

**🔴 CRITICAL** — Immediate response required (< 1 hour)
- Repository deletion or data loss
- Force push to main branch destroying history
- Malicious code pushed to main branch
- Account compromise with active malicious activity
- Public disclosure of unpatched critical vulnerability

**🟠 HIGH** — Rapid response required (< 4 hours)
- Branch protection bypassed
- Unauthorized merge of pull requests
- Suspicious commit activity
- Private information accidentally committed
- Organizational access compromised (no malicious activity yet)

**🟡 MEDIUM** — Timely response required (< 24 hours)
- Spam or abuse in issues/PRs
- Accidental deletion of non-critical content
- Minor misconfigurations
- Reputation concerns (misinformation, confusion)

**🟢 LOW** — Routine response (< 1 week)
- Documentation errors
- Minor policy violations
- Community conduct issues

---

## 🎯 Incident Procedures

### 1. Account Compromise

**If your GitHub account is compromised:**

#### Immediate Actions (within minutes)
1. **Change GitHub password** → https://github.com/settings/security
2. **Revoke all personal access tokens** → https://github.com/settings/tokens
3. **Revoke all SSH keys** → https://github.com/settings/keys
4. **Revoke all authorized GitHub Apps** → https://github.com/settings/apps
5. **Review recent sessions** → https://github.com/settings/sessions (revoke suspicious ones)
6. **Enable additional security** → Ensure 2FA is working correctly

#### Within 1 Hour
7. **Contact GitHub Support** → Report the compromise
8. **Notify community** → Post issue explaining situation
9. **Review recent commits** → Check for unauthorized changes
10. **Audit organization access** → Remove any suspicious members/collaborators

#### Within 4 Hours
11. **Rotate all credentials** → Any API keys, tokens, or secrets (if any exist)
12. **Update incident response plan** → Document lessons learned

#### Recovery
13. **Change all linked accounts** → Email, other services with same password
14. **Monitor for fallout** → Watch for suspicious activity on linked accounts
15. **Post-incident review** → What happened? How to prevent recurrence?

---

### 2. Repository Compromise

**If the repository is attacked (force push, malicious merge, deletion):**

#### Immediate Actions
1. **Assess damage** → What happened? What's affected?
2. **Lock repository** → Settings → Options → Make private temporarily (if needed)
3. **Notify community** → Post issue with CRITICAL tag

#### Recovery via Git Reflog
```bash
# Locally clone the repository
git clone git@github.com:agent-currency/proof-of-intelligence.git recovery
cd recovery

# Check reflog for recent states
git reflog

# Find the commit before the incident
git reset --hard <commit-hash>

# Force restore to GitHub
git push origin main --force
```

#### Recovery from Backup
If reflog is insufficient:
1. **Restore from backup** → Use mirror clone or offsite backup
2. **Verify integrity** → Check that all content is present
3. **Push restored version** → `git push origin main --force`
4. **Compare timestamps** → Ensure you're restoring to the right state

#### After Recovery
5. **Enable branch protection** → Prevent future force pushes
6. **Review all changes** → Ensure nothing malicious remains
 7. **Update access controls** → Remove unauthorized collaborators
8. **Postmortem** → Document and share with community

---

### 3. Private Information Exposed

**If secrets, credentials, or private data are accidentally committed:**

#### Immediate Actions
1. **Assess severity** → What type of data? How sensitive?
2. **DO NOT just remove from git** → The data is still in history
3. **Rotate affected credentials** → Assume they're compromised

#### Removal Procedure
**For minor info (email, name):**
- Commit a fix removing the data
- Document in commit message

**For secrets (API keys, tokens):**
1. **Rotate immediately** → Revoke and regenerate
2. **Bypass repository** → Contact GitHub Support directly for history removal
3. **Force push to all branches** → Ensure it's gone everywhere
4. **Consider repository rotation** → In extreme cases, delete and recreate

#### Prevention
- **Enable secret scanning** → Repository settings (free for public repos)
- **Add pre-commit hooks** → Scan for secrets before commit
- **Use .gitignore** → Prevent committing sensitive files
- **Education** → Document best practices in CONTRIBUTING.md

---

### 4. Malicious Pull Request or Issue

**If someone submits malicious code or spam:**

#### Immediate Actions
1. **Close PR/Issue** → Immediately close
2. **Lock conversation** → Prevent further comments
3. **Report to GitHub** → Use reporting tools
4. **Block user** → If repeated abuse

#### For Malicious Code
5. **Do NOT merge** → Obviously
6. **Analyze the code** → Understand what it was trying to do
7. **Document the attack** → Create security advisory if pattern emerges
8. **Warn community** → Post issue describing the attack

#### Prevention
- **Require PR reviews** → At least 1 reviewer before merge
- **Enable CI checks** → Automated testing
- **Code review guidelines** → Document in CONTRIBUTING.md
- **Sandbox review environment** → Don't run untrusted code locally

---

### 5. Organization Security Issues

**If organization access or settings are compromised:**

#### Immediate Actions
1. **Review all members** → Organization settings → Members
2. **Remove suspicious accounts** → Immediately remove access
3. **Audit outside collaborators** → Check for unauthorized additions
4. **Review OAuth apps** → Revoke suspicious apps
5. **Check repository settings** → Ensure visibility, permissions are correct

#### Recovery
6. **Re-enable security features** → 2FA, branch protection, etc.
7. **Audit all repositories** → Not just this one, check all org repos
8. **Update org policies** → Base permissions, default settings
9. **Document incident** → What happened? What changed?

---

### 6. Public Misinformation or Confusion

**If there's confusion, misinformation, or reputation concerns:**

#### Actions
1. **Assess source** → Where is this coming from?
2. **Determine severity** → Is this causing harm?
3. **Craft response** → Clear, factual, professional
4. **Post publicly** → Use GitHub Issues or Discussions
5. **Monitor** → Track sentiment and response

#### Principles
- **Respond once** → Don't get drawn into extended debates
- **Stay professional** → Don't escalate
- **Stick to facts** → Correct misinformation with evidence
- **Know when to ignore** → Not all criticism warrants response

---

## 🔄 Recovery Checklist

After any incident, complete this checklist:

### Immediate (0-1 hour)
- [ ] Incident contained and stopped
- [ ] Damage assessed
- [ ] Community notified (if public)
- [ ] Credentials rotated (if applicable)

### Short-term (1-24 hours)
- [ ] Full recovery completed
- [ ] Security controls hardened
- [ ] Incident documented (what happened, timeline, impact)
- [ ] Prevention measures identified

### Long-term (1-7 days)
- [ ] Post-incident review completed
- [ ] Lessons learned documented
- [ ] Incident response plan updated
- [ ] Community updated on resolution
- [ ] Security improvements implemented

---

## 📞 Communication Plan

### Internal (Project Maintainers)
- Use GitHub issues with `security` label
- Direct email for urgent matters
- Document all decisions

### External (Community)
- **Transparent** → Share what happened, what's affected
- **Timely** → Communicate early, update often
- **Actionable** → Tell users what they need to do
- **Professional** → Stay calm, factual, focused on resolution

### Communication Channels
- **GitHub Issues** → Primary channel for updates
- **Repository README** → Add banner during active incidents
- **Organization page** → Update if org-wide issue

---

## 🛡️ Prevention Measures

### Technical Controls
- **Branch protection** → Enabled for main branch
- **Secret scanning** → Enabled for repository
- **2FA required** → For organization admins
- **Minimal access** → Principle of least privilege
- **Regular backups** → Offsite mirror clones

### Process Controls
- **Code review required** → At least 1 reviewer
- **CI/CD checks** → Automated testing before merge
- **Security audits** → Before mainnet launch
- **Regular access reviews** → Who has access to what?
- **Incident response practice** → Run through scenarios

### Monitoring
- **GitHub Dependabot** → Alert on vulnerabilities
- **GitHub Security Advisories** → Track and publish fixes
- **Repository analytics** → Watch for unusual activity
- **Community sentiment** → Monitor issues and discussions

---

## 📚 Resources

### GitHub Security
- [GitHub Security Documentation](https://docs.github.com/en/security)
- [Securing your account](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure)
- [Best practices for securing repositories](https://docs.github.com/en/code-security/getting-started/best-practices-for-securing-repositories)

### Incident Response
- [Incident response fundamentals](https://www.sans.org/white-papers/incident-handling/incident-handlers-handbook/)
- [Post-incident review template](https://github.com/github/github-incident-response/tree/master/templates)

### Community
- [Reporting vulnerabilities to GitHub](https://bounties.github.com/)

---

**Remember:** The goal of incident response is not just to recover, but to learn and improve. Every incident is an opportunity to harden the project against future attacks.

---

*Last updated: 2026-01-31*
*Version: 1.0*

**Next review date:** 2026-02-28 (monthly review recommended)
