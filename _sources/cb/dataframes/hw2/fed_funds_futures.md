# Dataframe: `hw2:fed_funds_futures` - 30-Day Fed Funds Futures (ZQ)

Daily bars (Databento schema `ohlcv-1d`) from the CME Globex dataset `GLBX.MDP3`, pulled with parent symbology (`ZQ.FUT`) so that one request returns every listed ZQ contract. Each row is one contract on one trading day: `date` is the trading date and `symbol` the contract, for example ZQV6 for October 2026. The pull also returns calendar spreads (ZQU6-ZQZ6) and butterflies (ZQ:BF K6-M6-N6); keep the outright months with `fedwatch.filter_outright_contracts`. A contract settles at 100 minus the average daily effective federal funds rate over its month, so 100 minus the close is the market's forecast of that month's average rate. Thinly traded months can go days without a bar, so `fedwatch.latest_prices_by_contract` takes each contract's latest close. The window is the trailing 180 days unless `START_DATE` and `END_DATE` are set in `.env`. The data is free under the course's Databento subscription, and the pull checks that the cost estimate is $0.00 before it downloads anything.


## DataFrame Glimpse

```
Rows: 11737
Columns: 7
$ date   <datetime[ns]> 2026-10-21 00:00:00
$ symbol          <str> 'ZQ:BF X6-Z6-F7'
$ open            <f64> 8.0
$ high            <f64> 8.5
$ low             <f64> 8.0
$ close           <f64> 8.5
$ volume          <u64> 101


```

## Dataframe Manifest

| Dataframe Name                 | 30-Day Fed Funds Futures (ZQ)                                                          |
|--------------------------------|--------------------------------------------------------------------------------------|
| Dataframe ID                   | [fed_funds_futures](../dataframes/hw2/fed_funds_futures.md)                                       |
| Sources                        | CME Group                                          |
| Providers                      | Databento                                        |
| Provider Links                 | https://databento.com/datasets/GLBX.MDP3                                   |
| Tags                           | Monetary Policy, Futures, Fed Funds                                             |
| Access Types                   |                                       |
| How is data pulled?            | Databento API via Python                                                   |
| Data available up to (min)     | 2026-10-21 00:00:00                                                             |
| Data available up to (max)     | 2026-10-21 00:00:00                                                             |
| Dataframe Path                 | /root/hfelgenhauer/FINM32800/hw2-hfelgenhauer/_data/fed_funds_futures.parquet                                             |


**Linked Charts:**


- [hw2:fedwatch_latest_forecast](../../charts/hw2.fedwatch_latest_forecast.md)



## Pipeline Manifest

| Pipeline Name                   | HW 2: The Yield Curve and the Policy Path                       |
|---------------------------------|--------------------------------------------------------|
| Pipeline ID                     | [hw2](../../../index.md)              |
| Maintainer                      | Jeremiah Bejarano               |
| Contributors                    | Jeremiah Bejarano |
| Repository                     | https://github.com/hw-finm-32800/hw2                  |
| Pipeline Web Page               | <a href="file:///root/hfelgenhauer/FINM32800/hw2-hfelgenhauer/docs/index.html">Pipeline Web Page      |
| Date of Last Code Update        | 2026-10-22 19:26:38           |
| OS Compatibility                | Windows, Linux, macOS |
| Linked Dataframes               |  [hw2:crsp_treasury_consolidated](../../dataframes/hw2/crsp_treasury_consolidated.md)<br>  [hw2:fed_yield_curve](../../dataframes/hw2/fed_yield_curve.md)<br>  [hw2:fed_funds_futures](../../dataframes/hw2/fed_funds_futures.md)<br>  |


**Build Commands:**
```
doit

```

