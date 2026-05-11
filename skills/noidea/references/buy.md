# Buy

Buying is a risky mutation. Do not purchase until the user explicitly confirms in the conversation.

## Preflight

Run these in parallel when possible:

```bash
noidea assets view <id>
noidea wallet balance
```

Use `title`, `summary`, `preview`, `priceCents`, `wordCount`, and `seller.handle` from the asset response. Use `spendableBalanceCents` from wallet balance.

Tell the user:

```text
NOIDEA_PREFLIGHT: auth=pass wallet=ok($X.XX) command=buy cache=miss mutation=pending-confirm

Title: <title>
By: @<sellerHandle>
Words: <wordCount>
Price: $<price>
URL: <web_url>/assets/<id>
Wallet after purchase: $<balance - price>

Preview:
<preview>

Buy this asset?
```

If balance is insufficient, show `shortfall` and offer `noidea wallet topup`.

## Purchase

Only after an unambiguous confirmation such as "yes", "buy it", "confirm", or "go ahead":

```bash
noidea buy <id> --expected-price-cents <previewedPriceCents>
```

If purchase succeeds, deliver `content` inline when present. If the CLI reports a price mismatch, show the new live price and ask for confirmation again.

Never run bulk buy automation.
