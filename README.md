<br />
<br />

```mermaid
graph LR

A(AMP <br /> Source)
A -->|Send Message to <br/> API Gateway| B[AMP SQS Queue]
B -->|Messgae Processing| C[AMP Event Worker]
C -->|Calls POQ| D(POQ)
D -->E{POQ <br /> Outcome?}
E -->|POQ Call <br />Successful| F(AMP)
E -->|POQ Call <br />Failure| G[AMP SQS DLQueue]
G -->|Re-Process Message| B[AMP SQS Queue]
```


<br />
<br />
<br />
<br />
<br />

```mermaid
graph LR

A(Rocket Logic Docs Source)

A --> B[Process Doc Extraction Event]

B --> C{Event Type?}
C -->|Issue Event| D(POQ - ISSUE)
C -->|Complete Event| E(POQ - COMPLETE)
D -->|Call AMP to Update TI 4725| F(AMP)
E -->|Create Payoff and save to AMP| F(AMP)
```

```mermaid
sequenceDiagram
    participant dotcom
    participant iframe
    participant viewscreen
    dotcom->>iframe: loads html w/ iframe url
    iframe->>viewscreen: request template
    viewscreen->>iframe: html & javascript
    iframe->>dotcom: iframe ready
    dotcom->>iframe: set mermaid data on iframe
    iframe->>iframe: render mermaid
```
