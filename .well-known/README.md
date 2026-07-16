# .well-known

`oauth-authorization-server` is the RFC 8414 metadata document for the OAuth 2.1
authorization server that lets ChatGPT connect to CalFitness
(`docs/planning/CHATGPT_INTEGRATION_PLAN.md`, Phase 2b).

**Why it lives in a static site rather than next to the code that implements it.**
RFC 8414 derives the document's URL from the issuer: for an issuer with a path,
the well-known segment is *inserted* between host and path. An issuer of
`<ref>.supabase.co/functions/v1/oauth` would need its document at supabase.co's
root — which we cannot serve. §3.3 then forbids the obvious workaround: the
`issuer` in the document MUST equal the issuer used to fetch it.

So the issuer is this origin — `https://calfitness.github.io`, path-less, stable,
HTTPS — and it serves the document. The endpoints it advertises run as Supabase
edge functions. Nothing in RFC 8414 requires them to share a host.

**Two things this depends on, both verified:**

- Vite copies dot-directories out of `public/`, so this reaches `dist/`.
- `deploy.sh` writes `.nojekyll`. Without it GitHub Pages hides `.well-known`
  entirely, and discovery would 404 with no obvious cause.

**Keep the issuer path-less.** If it ever gains a path, clients will look for this
document somewhere we don't publish it and the whole flow breaks with a confusing
error. There's a test pinning that invariant in
`backend/supabase/functions/_shared/oauth.test.ts`.

**Editing:** this file is static because the endpoint URLs never change. If they
do, change them here *and* in the `oauth` edge function's fallback metadata
handler, which serves the same document for clients that probe the endpoint host.
