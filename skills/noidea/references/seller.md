# Seller

Use for seller status, earnings, payouts, and owned assets.

## Commands

```bash
noidea seller dashboard
noidea seller payouts --limit 20
noidea assets mine --status published
```

For payout creation, treat it as a risky mutation. Show amount, payout type, available balance, and fees when known; wait for explicit confirmation before running:

```bash
noidea seller payout --amount <cents> --payout-type standard
```

If seller access fails, check:

```bash
noidea status
```

If `isSeller` is false, direct the user to `<web_url>/become-seller`.
