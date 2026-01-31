# Backup Procedures

This document explains how to back up and restore the Proof of Intelligence repository.

---

## 🔒 Automated Backups

### Mirror Clone (Recommended)

Create a bare mirror clone containing all repository history:

```bash
# Create mirror backup
cd /path/to/backups
git clone --mirror https://github.com/agent-currency/proof-of-intelligence.git proof-of-intelligence-backup

# Update backup periodically
cd proof-of-intelligence-backup
git remote update
```

**Advantages:**
- Contains full repository history
- Small (bare repository, no working copy)
- Easy to update
- Can be restored from

**Location:** `/tmp/proof-of-intelligence-backup` (temporary, move to permanent location)

---

## 🔄 Backup Schedule

### Recommended Frequency
- **Automated:** Daily (cron job or GitHub Action)
- **Manual:** Before major changes (branch merges, releases)

### Update Procedure
```bash
# Navigate to backup directory
cd /path/to/backups/proof-of-intelligence-backup

# Fetch latest changes
git remote update

# Verify update worked
git log -1 --oneline
```

---

## 💾 Offsite Backup Options

### Option 1: GitLab Mirror
```bash
# Create mirror on GitLab
git clone --mirror https://github.com/agent-currency/proof-of-intelligence.git
cd proof-of-intelligence.git
git remote add gitlab https://gitlab.com/[user]/proof-of-intelligence.git
git push --mirror gitlab
```

### Option 2: Bitbucket Mirror
```bash
# Create mirror on Bitbucket
git clone --mirror https://github.com/agent-currency/proof-of-intelligence.git
cd proof-of-intelligence.git
git remote add bitbucket https://bitbucket.org/[user]/proof-of-intelligence.git
git push --mirror bitbucket
```

### Option 3: Archive (tar.gz)
```bash
# Create compressed archive
git clone https://github.com/agent-currency/proof-of-intelligence.git
tar -czf proof-of-intelligence-$(date +%Y%m%d).tar.gz proof-of-intelligence/
```

---

## 🚨 Recovery Procedures

### Scenario 1: Repository Deleted

If the GitHub repository is accidentally deleted:

```bash
# GitHub can recover within 90 days
# Contact GitHub Support immediately

# If recovery fails, recreate from backup:
cd /path/to/backups/proof-of-intelligence-backup
git push --mirror git@github.com:agent-currency/proof-of-intelligence.git
```

### Scenario 2: Accidental Force Push

If someone force pushes and destroys history:

```bash
# Use git reflog to recover
cd proof-of-intelligence
git reflog

# Find the commit before the force push
git reset --hard <commit-hash>

# Force restore to GitHub
git push origin main --force
```

### Scenario 3: Complete Loss of GitHub Access

If GitHub is completely unavailable:

1. **Restore from backup** to alternative hosting (GitLab, Bitbucket)
2. **Update DNS/custom domain** to point to new location
3. **Notify community** via alternative channels
4. **Continue work** on new platform

---

## ✅ Backup Checklist

### Initial Setup
- [ ] Create mirror backup directory
- [ ] Set up automated backup schedule (cron or GitHub Action)
- [ ] Document backup location
- [ ] Test restore procedure
- [ ] Store backup credentials securely

### Ongoing Maintenance
- [ ] Verify backups are updating (check weekly)
- [ ] Test restore procedure periodically (monthly)
- [ ] Rotate backup credentials (quarterly)
- [ ] Review backup location security (quarterly)

---

## 📁 Current Backup Status

**Last backup created:** 2026-01-31 16:18 UTC  
**Backup location:** `/tmp/proof-of-intelligence-backup` (temporary)  
**Backup type:** Mirror clone (bare repository)  
**Status:** ✅ Initial backup complete

**Next actions:**
- [ ] Move to permanent backup location
- [ ] Set up automated daily updates
- [ ] Create offsite mirror (GitLab or Bitbucket)
- [ ] Document automated backup script

---

## 🔐 Security Considerations

1. **Backup access:** Protect backup credentials same as GitHub credentials
2. **Backup location:** Store backups in secure, access-controlled location
3. **Encryption:** Consider encrypting backup archives for sensitive repos
4. **Retention:** Keep multiple backup generations (daily, weekly, monthly)
5. **Testing:** Regularly test restore procedures to verify backups work

---

**Remember:** A backup you haven't tested restoring from is not a backup.

---

*Last updated: 2026-01-31*
