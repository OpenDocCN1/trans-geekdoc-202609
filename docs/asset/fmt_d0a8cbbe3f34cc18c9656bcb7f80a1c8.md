
```latex
\begin{tikzpicture}[line join=round,font=\font{T1}{m}{n}]

\tikzset{

Line/.style={Brown!60, -width=6pt, length=6pt},

Box/.style={innersep=2pt, ysep=2pt, distance=0.5, draw=RedLine, line width=0.75pt, fill=RedL!60, align=center, text width=37mm, minimum width=37mm, height=15.5mm},

Box2/.style={draw=GreenD,fill=GreenL},

Box3/.style={draw=VioletLine,fill=VioletL},

Box4/.style={draw=VioletLine,fill=VioletL2},

Box5/.style={draw=BlueLine,fill=BlueL!50},

Box6/.style={draw=OrangeLine,fill=OrangeL!50}

}

\node(B1){Data Layer: DP, FL, Encryption};

\node(B2)[right=of B1]{Model Layer: Robustness, Watermarking, Secure Deployment};

\node(B3)[right=of B2]{Runtime Layer: Input Validation, Output Monitoring};

\node(B4)[right=of B3]{Hardware Layer: TEEs, Secure Boot, PUFs};

\node(B22)[above=0.7 of B2]{Select Defenses Across the Stack};

\node(B23)[above=0.7 of B22]{Assess Threat Model & Deployment Context};

\node(B44)[below=0.7 of B4]{Plan for Runtime Adaptation and Recovery};

\node(B45)[below=0.7 of B44]{Rollback, Isolation, Incident Response};

\node(B46)[left=of B45]{Monitoring, Logging, Alerting};

\node(B47)[right=of B45]{Design Feedback Loop};

\drawLine--(B22);

\drawLine--(B2);

\drawLine|(B1);

\drawLine|(B3);

\drawLine|(B4);

\drawLine--(B44);

\drawLine|(B46);

\drawLine|(B47);

\drawLine--(B45);

\end{tikzpicture}
```
