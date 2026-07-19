# DEXTools chart widget

(This is the public documentation repo of the DEXTools Chart Widget)

The **Chart Widget** allows websites to display an embedded trading chart for any pool supported by [DEXTools.io](https://www.dextools.io) app. Chart data is 
updated in real-time, including the current price in USD and trade history.

https://www.dextools.io/widget-chart/en/ether/pe-light/0xa29fe6ef9592b5d408cca961d0fb9b1faf497d6d?theme=dark

<img width="892" height="535" alt="widget screenshot" src="https://github.com/user-attachments/assets/105f0203-8f4b-4246-8c2a-fe32aea7c9c4" />

Chart display is provided by [TradingView](https://www.tradingview.com/)

## Get your pool/token iframe widget code

1) First search your favorite token or pool by address, name... using the [DEXTools search bar](https://www.dextools.io/app/).

<img width="1127" height="315" alt="search screenshot" src="https://github.com/user-attachments/assets/108969c7-596a-4482-8976-f11fef4a1d5b" />


2) Then click the **embed** option of the [DEXTools pair explorer](https://www.dextools.io/app/en/ether/pair-explorer/0xa29fe6ef9592b5d408cca961d0fb9b1faf497d6d), a pop-up will appear to configure the chart and copy the embed code.

<img width="376" height="375" alt="embed screenshot" src="https://github.com/user-attachments/assets/c99decc2-00ac-479b-8898-ca074eb55110" />


## Quick Example

An iframe based integration example follows:
```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DEXTools Trading Chart</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #121212;
            color: #ffffff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }
        h2 {
            margin-bottom: 20px;
            color: #2962FF;
        }
        .chart-container {
            width: 100%;
            max-width: 1000px;
            height: 600px;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
            border: 1px solid #333333;
            background-color: #1e222d;
        }
        iframe {
            width: 100%;
            height: 100%;
            border: none;
        }
    </style>
</head>
<body>

    <h2>Live Trading Chart</h2>
    
    <div class="chart-container">
        <!-- DEXTools Widget Link -->
        <iframe 
            id="dextools-widget"
            title="DEXTools Trading Chart"
            src="https://www.dextools.io/widget-chart/en/ether/pe-light/0xa29fe6ef9592b5d408cca961d0fb9b1faf497d6d?theme=dark&chartType=1&chartResolution=60&drawingToolbars=true&showTradeHistory=true&tvPlatformColor=1e222d&tvPaneColor=131722&headerColor=2962FF">
        </iframe>
    </div>

</body>
</html>

```

## Common issues and testing

You can test if the IFrame integration works properly with a tool like [https://iframetester.com/](https://iframetest.com/).

In case of errors showing a Chart in your website, please check your CSP policy for IFrame content https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options

Please be aware that USE OF CHART WIDGET IFRAME FROM **localhost** WON'T WORK, please use a real domain instead.

## Customization options

The widget is configured by using the embed wizard, but also manually adjusting the following parts and query parameters of this URL:

```
https://www.dextools.io/widget-chart/en/<chainId>/pe-light/<pairAddress>?theme=<theme>&chartType=<chartType>&chartResolution=<chartResolution>&drawingToolbars=<drawingToolbars>&tvPlatformColor=<color>&tvPaneColor=<color>&headerColor=<color>&chartInUsd=<chartInUsd>&showTradeHistory=<showTradeHistory>&tradeHistoryColor=<tradeHistoryColor>
```

| Parameter        | Values                                                                                                                                                |
|------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| chainId          | blockchain ID (see [list below](#supported-blockchains))                                                                                              |
| pairAddress      | address of the pool to display                                                                                                                        |
| theme            | `dark` or `light`                                                                                                                                     |
| chartType        | 0 = Bar<br/>1 = Candle<br/>2 = Line<br/>3 = Area<br/>8 = Heikin Ashi<br/>9 = hollow candle<br/>10 = Baseline                                          |
| chartResolution  | 1 (minute), 3, 5, 15, 30, 60, 120, 240, 720, 1D, 3D, 1W, 1M                                                                                           |
| drawingToolbars  | `false` or `true`                                                                                                                                     |
| showTradeHistory | `false` or `true`                                                                                                                                     |
| headerColor      | custom color for the widget header.<br/>**IMPORTANT: should be in hexadecimal format without the `#`**                                                |
| tvPlatformColor  | custom color for the chart background.<br/>**IMPORTANT: should be in hexadecimal format without the `#`**                                             |
| tvPaneColor      | custom color for the chart controls background.<br/>**IMPORTANT: should be in hexadecimal format without the `#`**                                    |
| tradeHistoryColor| custom color for the trade history background.<br/>**IMPORTANT: should be in hexadecimal format without the `#`**                                     |
| chartInUsd       | `false` to show the "Token/\<chain reference token\>" chart, otherwise (also if this param is not passed) the chart is the "Token/USD" one by default |


## Supported blockchains

We add support for new blockchains frequently. This is the current list of available blockchains:

| Blockchain | ID |
| :--- | :--- |
| SOLANA | solana |
| ETHEREUM | ether |
| BNB | bnb |
| BASE | base |
| POLYGON | polygon |
| PULSE | pulse |
| TON | ton |
| ARBITRUM | arbitrum |
| AVALANCHE | avalanche |
| MONAD | monad |
| RONIN | ronin |
| SUI | sui |
| SONIC | sonic |
| TRON | tron |
| CRONOS | cronos |
| XRPL | xrpl |
| WORLD CHAIN | worldchain |
| OSMOSIS | osmosis |
| ABSTRACT | abstract |
| VSC | vsc |
| SONEIUM | soneium |
| LINEA | linea |
| OPTIMISM | optimism |
| ICP | icp |
| HYPER EVM | hyperevm |
| BERA CHAIN | berachain |
| X LAYER | xlayer |
| CHILIZ | chiliz |
| SHIBARIUM | shib |
| HEDERA | hedera |
| APTOS | aptos |
| MANTLE | mantle |
| UNI CHAIN | unichain |
| SHIDO | shido |
| FLARE | flare |
| METIS | metis |
| DOGE CHAIN | dogechain |
| ZKSYNC | zksync |
| STORY | story |
| KAIA | kaia |
| NEAR | near |
| INK | ink |
| CELO | celo |
| PLASMA | plasma |
| SEI | sei |
| XDC | xdc |
| GNOSIS | gnosis |
| APE CHAIN | apechain |
| IOTA-EVM | iotaevm |
| BLAST | blast |
| INJECTIVE | injective |
| QUBIC | qubic |
| ETHERLINK | etherlink |
| PAW CHAIN | pawchain |
| FUSE | fuse |
| U2U | utwou |
| ODYSSEY | odyssey |
| SCROLL | scroll |
| CRONOS-ZKEVM | cronoszkevm |
| SUPERSEED | superseed |
| OKTC (FORMER OEC) | oktc |
| ARBITRUM NOVA | arbitrumnova |
| BITLAYER | bitlayer |
| ELYSIUM | elysium |
| GRAVITY ALPHA | gravityalpha |
| MODE | mode |
| MANTA | manta |
| KAVA | kava |
| KUJIRA | kujira |
| POLYGON-ZKEVM | polygonzkevm |
| UNIT ZERO | units |
| NIBIRU | nibiruevm |
| ANUBIS | anubis |
| TERRA | terra |
| ROBINHOOD | robinhood |

```
================================================================================
                          CEASE AND DESIST NOTICE
                 COPYRIGHT INFRINGEMENT & DEMAND FOR TAKEDOWN
================================================================================

TO:      The Management of [Insert Infringing Website Name/URL Here]
FROM:    Danial Zivehdar
DATE:    July 19, 2026
SUBJECT: URGENT: Unauthorized Use of Intellectual Property and Demand for 
         Immediate Removal

Dear Sir/Madam,

This is a formal legal notice to inform you that your website has engaged in 
the unauthorized copying, replication, and use of the design, patterns, links, 
and content belonging to me, Danial Zivehdar. 

COMPREHENSIVE RIGHTS RESERVATION:
Please be formally notified that under the website's governing terms and 
applicable intellectual property laws, I retain exclusive and absolute ownership 
of ALL rights, titles, and interests regarding this project. This includes, 
but is not limited to, the website contract/terms, all designs, templates, 
hyperlinks, source codes, and absolutely ALL associated content and digital 
assets (hereinafter referred to as "the Protected Assets"). Any unauthorized 
use, reproduction, or distribution of these Protected Assets constitutes a 
material breach of copyright, contractual terms, and digital property laws.

Therefore, you are hereby formally demanded to take the following actions 
within 12 hours [or specify 12 days] from the receipt of this notice:

1. IMMEDIATE CESSATION: Immediately cease and desist from any further use, 
   display, or distribution of the Protected Assets.
   
2. COMPLETE DATA SANITIZATION: Permanently delete and purge all copied files 
   and assets from your servers, virtual environments, mobile device storage, 
   and any other associated data storage systems without exception.
   
3. WEBSITE TAKEDOWN: Immediately shut down or disable access to the infringing 
   sections of your website until the violations are fully resolved and a 
   final legal determination is made.

Please be advised that failure to comply with this notice within the stipulated 
timeframe will leave me with no choice but to pursue all available legal 
remedies. This includes, but is not limited to, filing formal complaints with 
the relevant judicial authorities and cyber police, as well as submitting a 
formal DMCA/copyright infringement report to your Hosting Provider and Domain 
Registrar to request the immediate suspension and takedown of your entire 
website.

Furthermore, be advised that no informal guarantees, settlements, or 
communications will be entertained regarding this matter. Any necessary 
correspondence will be conducted strictly through official legal channels.

All of my legal rights and remedies are expressly reserved.

Sincerely,

----------------------------------------
Danial Zivehdar
Phone: +98 9197159411
Email: danialzivehdar1992@gmail.com
----------------------------------------
================================================================================
