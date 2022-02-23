```mermaid
flowchart TB

A(AMP <br /> Source)
A -->|Send Message to <br/> API Gateway| B[AMP SQS Queue]
B -->|Messgae <br />Processed| C[AMP <br /> Event Worker]
C -->|Calls POQ| D(POQ)
D -->E{POQ <br /> Outcome?}
E -->|<br />Successful <br /><br /> Call AMP Endpoint with Results and Exceptions| F(AMP)
F -->|Finalize| COMPLETE(<font size=5>COMPLETE)
E -->|<br />Failure <br /><br />Re-Process message with Dead Letter Queue| G[AMP SQS DLQueue]
G -->|Re-Process Message| B[AMP SQS Queue]

%% CSS Styles
style A fill:#f9f,stroke:#333,stroke-width:4px
style F fill:#bbf,stroke:#f66,stroke-width:2px,padding:20px
style COMPLETE fill:#FF0000,stroke:#f66,stroke-width:2px

%% Set the classes
classDef success fill:#8FD27F,stroke:#8FD27F;
classDef flow fill:#A2C3FB,stroke:#A2C3FB;
classDef quest fill:#FABE78,stroke:#FABE78;

%% Assign the classes
class A success;
class B flow;
class C quest;
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
