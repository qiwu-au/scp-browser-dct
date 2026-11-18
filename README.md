# Single-cell proteomics browser: mouse DCT cells, control and zero-K diet

Interactive browser for the single-cell proteomics (SCP-MS) data of mouse distal convoluted tubule (DCT) cells on a control diet (729 cells, 6,078 proteins) and on a zero-potassium (zero-K) diet (702 cells, 5,953 proteins). The browser shows each condition on its own and has one page that compares the two.

- Browser: https://scp-browser-dct.streamlit.app/
- All browsers and the methods: https://scp-browser-landing.streamlit.app/

The About page of the browser describes the data, the cell-type annotation and how the shown values are computed.

## Run locally

With Python 3.12:

```
pip install -r requirements.txt
streamlit run app.py
```

## Files

| path | content |
| --- | --- |
| `app.py` | entry file |
| `scp_browser/` | pages, figures and summaries (code shared with the kidney browser) |
| `configs/` | texts, label sets and the About page |
| `data/dct_control/` | browser data of the control cells |
| `data/dct_zerok/` | browser data of the zero-K cells |
| `data/dct_comparison/` | data of the comparison page |
| `requirements.txt` | pinned packages |
| `.streamlit/config.toml` | theme |

In each data folder, `data_dictionary.csv` describes the downloadable files and `build_info.json` lists the data sources with their checksums.
