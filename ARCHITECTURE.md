# Neurodiagnoses: Technical Architecture Document

## 1. The Dual-System Philosophy
The Neurodiagnoses ecosystem combines two distinct but complementary computational systems:
- **A "Glass-Box" Bayesian Engine:** For explainable, evidence-based **diagnosis**.
- **"Black-Box" Machine Learning Pipelines:** For data-driven **prognosis and risk prediction**.

## 2. Master Architecture Diagram
```mermaid
graph TD
    subgraph User Interaction
        direction LR
        UI(Gradio UI / app.py)
        CSV(Input: Cohort CSV)
    end

    subgraph "Private Engine: neurodiagnoses-engine"
        direction LR
        
        subgraph "Knowledge Layer"
            KB[Knowledge Bases (.csv)]
        end

        subgraph "Processing Layer"
            ORCH(Unified Orchestrator)
            BAYES(Bayesian Engine)
            ML_RISK(Risk Prediction Engine)
            ML_PROG(Prognosis Engine)
        end

        subgraph "Models & Data"
            MODELS[Pre-trained ML Models (.joblib)]
        end
    end

    subgraph "Output: Neurodegenerative Signature"
        OUT_DX(Classical Differential)
        OUT_ANNO(Tridimensional Annotation)
        OUT_RISK(Risk / Prognosis Assessment)
    end
    
    CSV --> UI; UI -- Patient Data --> ORCH;
    
    ORCH -- Calls --> BAYES & ML_RISK & ML_PROG;
    BAYES -- Reads --> KB;
    ML_RISK & ML_PROG -- Use --> MODELS;
    BAYES --> OUT_DX & OUT_ANNO;
    ML_RISK & ML_PROG --> OUT_RISK;
```

## 3. Component Breakdown
Detailed descriptions of each component can be found in `MANIFEST.md`.
---

## 4. Fundamentos CientÃ­ficos y Explicabilidad

La lÃ³gica y las decisiones de diseÃ±o de este motor no son arbitrarias. Se basan en conceptos cientÃ­ficos clave extraÃ­dos de la literatura de vanguardia.

Para mantener una trazabilidad completa entre la ciencia y el cÃ³digo, mantenemos una **Base de Conocimiento Explicativo (BCE)**. Este sistema documenta los papers fundamentales que inspiran nuestra arquitectura y los enlaza directamente a los componentes de software que los implementan.

> **Consulta la Base de Conocimiento Explicativo completa aquÃ­: [docs/explicability/explicability_kb.yaml](docs/explicability/explicability_kb.yaml)**
