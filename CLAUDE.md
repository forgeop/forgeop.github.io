# Project Rules

## GitHub Pages Deployment — MANDATORY

**NEVER use orphan branch + force push for GitHub Pages deploys.**

This pattern triggers GitHub's automated abuse/spam detection and causes account suspension:
```
# BAD — do not use
git init
git checkout --orphan main
git push --force origin main
```

**Always use incremental commits instead:**
```
# GOOD
git clone --depth=1 <repo> _deploy
# ... sync files ...
git diff --cached --quiet || git commit -m "Update site"
git push origin main
```

The force-push-every-deploy pattern looks identical to a compromised account
being used for spam. Incremental commits look like a normal developer workflow.
This applies to ALL GitHub Pages deployments in this project and any future ones.
