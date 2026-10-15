# MADT 7202 Mid-Term: which supplier pair should an analyst watch for shared risk?

Individual mid-term for MADT 7202 (Web and Social Network Analytics, NIDA).
Decision studied: which supplier pair joins a semiconductor analyst's shared-risk watchlist.
Data: 10-K filings of 27 chip, memory, cloud and server companies on SEC EDGAR (latest and prior year).
Network: bipartite filer -> supplier graph; supplier pairs scored by the filers that name both (NPMI primary, Jaccard as a check).

## Run it (no other files needed)

1. Open the notebook in Google Colab:
   `https://colab.research.google.com/github/apisitrtss-glitch/madt7202-supplier-network/blob/main/MADT7202_supplier_network.ipynb`
2. Runtime -> Run all.
3. The last section ("10. Check against the reported results") should print **All reported results reproduced.**

To check the other year, set `BACK = 1` in cell 1 and run again.

## Two run modes (`SOURCE` in cell 1)

| Mode | What it does |
|---|---|
| `"embedded"` (default) | Uses the labelled sentence table stored inside the notebook. Needs no internet. Gives the reported numbers. |
| `"live"` | Re-downloads the pinned 10-Ks from SEC EDGAR, re-extracts the sentences and says whether they match the embedded table. Put your own contact details in `USER_AGENT` first. |

## Files

| File | Purpose |
|---|---|
| `MADT7202_supplier_network.ipynb` | The analysis |
| `access_log.csv` | Log of the requests made to SEC EDGAR in my live run (optional evidence) |
| `core_pair_check_filled.csv` | Hand check of the evidence behind the recommended pair (if completed) |
| `precision_check_filled.csv` | Optional hand check of a random sample of labels (if completed) |

## Things to know

- **Context labels were assigned by Claude (an AI)**. They agree with a simple keyword rule on 83% of rows. They are embedded in the notebook (`LABELS_B64`) and can be read, changed and re-run.
- Sentences that are biographies of named executives are dropped at extraction (data minimisation).
- Data source: public filings on SEC EDGAR. Access: declared User-Agent, about 4 requests per second. SEC fair-access policy read on: **[add URL and date]**.
- Co-listing of two suppliers is not evidence that they fail together; the recommendation is a watchlist and stress-test candidate, not a prediction.
- Six filers (MSFT, GOOGL, AMZN, META, DELL, MPWR) are not pinned to a specific filing; they name no listed supplier in the pinned data, and `SOURCE = "live"` fetches their latest 10-K.
