# Agent HQ Development Pipeline

## Overview
Standard pipeline for Agent HQ SaaS projects: prototype → staging → production

## Pipeline Flow

### Stage 1: Prototype & Export (Lovable)
1. Develop feature/product prototype in Lovable
2. Export project design and assets
3. Extract GitHub export to local development environment
4. Create feature branch from `staging`

### Stage 2: Development & Testing (FORGE)
1. Rebuild/enhance prototype in Replit (full stack autonomy)
2. Run unit tests and integration tests
3. Commit to feature branch
4. Open pull request to `staging` branch
5. FORGE reviews and self-approves
6. Merge to `staging` (auto-deploy to staging environment)

### Stage 3: Staging Validation (bosgame CI/CD)
1. Staging environment runs automated tests
2. Manual QA validation (Joseph or QA team)
3. Performance and security checks
4. If all pass: approved for production promotion

### Stage 4: Production Deployment
1. Create pull request from `staging` to `main`
2. Code review and approval (Joseph + FORGE)
3. Merge to `main` branch
4. Automatic deployment to production via Vercel/bosgame
5. Monitor for errors; rollback if needed

## Branch Strategy

- **main:** Production-ready code. Protected branch. Requires PR + review.
- **staging:** Pre-production testing environment. Auto-deploys on merge.
- **feature/*:** Feature branches for development. Merge to staging via PR.

## Deployment Configuration

- **Staging auto-deploy:** Vercel connected to `staging` branch
- **Production auto-deploy:** Vercel connected to `main` branch
- **Rollback:** Revert commit and push to trigger automatic re-deployment

## Tools & Services

- **Prototype:** Lovable (rapid iteration)
- **Development:** Replit (full-stack autonomy)
- **CI/CD:** GitHub Actions + Vercel + bosgame
- **Testing:** Jest/Vitest (unit), Playwright (E2E)
- **Monitoring:** Sentry, LogRocket (error tracking)

## Typical Timeline

- Prototype (Lovable): 2–4 hours
- Development (FORGE in Replit): 30–40 hours
- Staging validation: 4–8 hours
- Production deployment: 1–2 hours
- **Total:** ~2–4 days per feature

## Escalation & Rollback

- **If staging tests fail:** FORGE fixes on feature branch, re-commits, re-opens PR
- **If production error detected:** Joseph initiates rollback (revert commit to main)
- **Security issues:** Escalate to #axiom immediately; pause deployment

## Future Enhancements

- Load testing automation
- Canary deployment strategy
- Database migration automation
- Feature flags for gradual rollout
