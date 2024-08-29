# Design Documentation

## Table of Contents
1. [Overview](#overview)
2. [Data Flow Diagrams (DFDs)](#data-flow-diagrams-dfds)
   - [Context Level DFD (Level 0)](#context-level-dfd-level-0)
   - [Level 1 DFD](#level-1-dfd)
3. [Class Diagrams](#class-diagrams)
   - [Classes](#classes)
   - [Relationships](#relationships)


## Overview
This document provides a detailed design of the integration process for mailbox, internet search history, video watch history, and music playlist history into an ad server platform. The design includes both Data Flow Diagrams (DFDs) and Class Diagrams to represent the flow of data and the system’s structure.

## Data Flow Diagrams (DFDs)

### Context Level DFD (Level 0)

The Context Level DFD provides an overview of the entire system, showing how the main components interact with external entities.

#### **Entities:**
- **Users:** Provide data inputs such as mailbox, internet search history, video watch history, and music playlist history.
- **Ad Server:** Receives personalised ad content to serve to the users.

#### **Processes:**
- **Data Collection:** Collects raw data from users.
- **Data Processing:** Processes the raw data (e.g., NLP, Semantic Extraction).
- **Ad Generation:** Generates personalised ads based on processed data.
- **Ad Serving:** Serves ads to users based on their profiles.

#### **Data Stores:**
- **Raw Data Store:** Stores raw user data.
- **Processed Data Store:** Stores processed data ready for analysis.
- **Ad Content Store:** Stores generated ad content.

#### **Diagram Overview:**
- Users → [Data Collection] → Raw Data Store
- Raw Data Store → [Data Processing] → Processed Data Store
- Processed Data Store → [Ad Generation] → Ad Content Store
- Ad Content Store → [Ad Serving] → Ad Server
- Ad Server → Users (Personalised Ads)

### Level 1 DFD

The Level 1 DFD breaks down the main processes into more detailed subprocesses.

#### **Processes:**
- **1.0 Data Collection:**
  - 1.1 Mailbox Data Ingestion
  - 1.2 Search History Ingestion
  - 1.3 Video Watch History Ingestion
  - 1.4 Music Playlist History Ingestion

- **2.0 Data Processing:**
  - 2.1 Context Analysis
  - 2.2 Semantic Extraction
  - 2.3 Natural Language Pre-processing
  - 2.4 Morphological Analysis
  - 2.5 Lemmatisation

- **3.0 Ad Generation:**
  - 3.1 Content Parsing
  - 3.2 Behaviour Analysis
  - 3.3 Feature Extraction

- **4.0 Ad Serving:**
  - 4.1 Model Training & Optimisation
  - 4.2 Integration with Ad Server Platform

#### **Diagram Overview:**
- **1.0 Data Collection**
  - Each input source (Mailbox, Search History, etc.) → Corresponding Subprocesses (1.1, 1.2, etc.) → Raw Data Store
- **2.0 Data Processing**
  - Raw Data Store → Processing Subprocesses (2.1, 2.2, etc.) → Processed Data Store
- **3.0 Ad Generation**
  - Processed Data Store → Generation Subprocesses (3.1, 3.2, etc.) → Ad Content Store
- **4.0 Ad Serving**
  - Ad Content Store → Serving Subprocesses (4.1, 4.2) → Ad Server → Users

## Class Diagrams

The Class Diagram represents the static structure of the system by showing the system's classes, their attributes, methods, and the relationships among the objects.

### Classes

1. **User**
   - **Attributes:**
     - UserID
     - Email
     - SearchHistory
     - VideoWatchHistory
     - MusicPlaylistHistory
   - **Methods:**
     - ProvideData()
     - ReceiveAds()

2. **RawData**
   - **Attributes:**
     - DataID
     - EmailContent
     - SearchQueries
     - VideoMetadata
     - MusicMetadata
   - **Methods:**
     - StoreRawData()
     - RetrieveRawData()

3. **ProcessedData**
   - **Attributes:**
     - ProcessedID
     - ContextualInfo
     - SemanticEntities
     - Sentiment
     - Morphemes
     - Lemmas
   - **Methods:**
     - ProcessRawData()
     - AnalyseData()

4. **AdContent**
   - **Attributes:**
     - AdID
     - AdText
     - TargetAudience
     - RelevanceScore
   - **Methods:**
     - GenerateAd()
     - OptimiseAd()

5. **RecommendationEngine**
   - **Attributes:**
     - EngineID
     - ModelParameters
     - OptimisationCriteria
   - **Methods:**
     - TrainModel()
     - GenerateRecommendations()

6. **AdServer**
   - **Attributes:**
     - ServerID
     - AdInventory
     - RealTimeBidding
   - **Methods:**
     - ServeAd()
     - TrackPerformance()

7. **NLPProcessor**
   - **Attributes:**
     - ProcessorID
     - Algorithms (Context Analysis, Semantic Extraction, etc.)
   - **Methods:**
     - ApplyContextAnalysis()
     - PerformSemanticExtraction()
     - ApplyNLPModel()

### Relationships

- **User** has **RawData**.
- **RawData** is processed into **ProcessedData** by **NLPProcessor**.
- **ProcessedData** is used by **RecommendationEngine** to generate **AdContent**.
- **AdContent** is served by **AdServer** to **User**.
- **AdServer** collects feedback to refine **RecommendationEngine**.
