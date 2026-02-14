# Requirements Document: Project Mirror - Digital Persona Schema System

## Introduction

Project Mirror is an Identity Preservation Engine that digitizes a creator's unique style to prevent "Content Drift" - the phenomenon where creators lose their authentic voice as they scale. The system analyzes video content across four DNA pillars (Visual, Audio, Semantic, Behavioral) to create a mathematical baseline persona, then provides tools to detect drift, inject persona into new content, and adapt content across platforms while preserving identity.

## Glossary

- **System**: The Project Mirror platform
- **Persona_Schema**: A structured JSON representation of a creator's unique style across four DNA pillars
- **Baseline_Persona**: The mathematical average of a creator's top-performing content, stored as persona.json
- **Content_Drift**: Measurable deviation from a creator's established style patterns
- **DNA_Pillar**: One of four categories (Visual, Audio, Semantic, Behavioral) that define creator identity
- **Drift_Score**: A numerical metric indicating how far current content deviates from Baseline_Persona
- **Ingestion_Pipeline**: The process of downloading and splitting video content into analyzable components
- **Encoder**: The component that normalizes extracted data into Persona_Schema format
- **Vision_Bot**: Computer vision analyzer for visual attributes
- **Audio_Bot**: Acoustic analyzer for audio attributes
- **Text_Bot**: NLP analyzer for semantic attributes
- **Creator**: A content creator who uses the platform to analyze their content
- **Agency**: An organization managing multiple creators
- **Channel_Handle**: A unique identifier for a creator's content platform account

## Requirements

### Requirement 1: Video Content Ingestion

**User Story:** As a creator, I want to import my existing video content, so that the system can analyze my historical style patterns.

#### Acceptance Criteria

1. WHEN a Creator provides a Channel_Handle, THE System SHALL retrieve the most recent 50 videos from that channel
2. WHEN videos are retrieved, THE System SHALL separate each video into audio, visual frames, and transcript components
3. WHEN video retrieval fails, THE System SHALL return a descriptive error message indicating the failure reason
4. WHEN a channel has fewer than 50 videos, THE System SHALL process all available videos
5. THE System SHALL support both short-form and long-form video formats

### Requirement 2: Visual DNA Extraction

**User Story:** As a creator, I want the system to analyze my visual editing patterns, so that I can understand my visual signature.

#### Acceptance Criteria

1. WHEN visual frames are provided, THE Vision_Bot SHALL calculate cut_rate_per_min (shots per minute)
2. WHEN visual frames are provided, THE Vision_Bot SHALL extract the dominant color_palette
3. WHEN visual frames are provided, THE Vision_Bot SHALL classify camera_angles distribution
4. WHEN visual frames are provided, THE Vision_Bot SHALL measure face_presence percentage
5. WHEN visual frames are provided, THE Vision_Bot SHALL calculate avg_shot_length_sec
6. WHEN visual frames are provided, THE Vision_Bot SHALL calculate visual_density for sensory load measurement
7. WHEN visual frames are provided, THE Vision_Bot SHALL measure background_clutter as an authenticity indicator
8. WHEN visual frames are provided, THE Vision_Bot SHALL calculate jugaad_score combining clutter and quality metrics
9. THE Vision_Bot SHALL store all visual metrics in structured format

### Requirement 3: Audio DNA Extraction

**User Story:** As a creator, I want the system to analyze my audio patterns, so that I can understand my sonic signature.

#### Acceptance Criteria

1. WHEN audio is provided, THE Audio_Bot SHALL calculate avg_wpm (words per minute)
2. WHEN audio is provided, THE Audio_Bot SHALL measure pitch variance
3. WHEN audio is provided, THE Audio_Bot SHALL classify music_genre
4. WHEN audio is provided, THE Audio_Bot SHALL measure silence_gap patterns
5. WHEN audio is provided, THE Audio_Bot SHALL calculate auditory_density for sensory load measurement
6. WHEN audio is provided, THE Audio_Bot SHALL measure audio_quality as a production quality indicator
7. THE Audio_Bot SHALL store all audio metrics in structured format

### Requirement 4: Semantic DNA Extraction

**User Story:** As a creator, I want the system to analyze my language patterns, so that I can understand my intellectual signature.

#### Acceptance Criteria

1. WHEN transcripts are provided, THE Text_Bot SHALL identify recurring catchphrases
2. WHEN transcripts are provided, THE Text_Bot SHALL classify hook_style patterns
3. WHEN transcripts are provided, THE Text_Bot SHALL extract topic_clusters
4. WHEN transcripts are provided, THE Text_Bot SHALL measure sentiment (valence and arousal)
5. WHEN transcripts are provided, THE Text_Bot SHALL identify narrative_structure patterns
6. WHEN transcripts are provided, THE Text_Bot SHALL calculate desi_meter score for cultural authenticity
7. WHEN transcripts are provided, THE Text_Bot SHALL measure hinglish_frequency as a code-mixing indicator
8. WHEN transcripts are provided, THE Text_Bot SHALL calculate switches_per_minute for language switching frequency
9. WHEN transcripts are provided, THE Text_Bot SHALL identify cultural_markers and local_references
10. THE Text_Bot SHALL store all semantic metrics in structured format

### Requirement 5: Behavioral DNA Extraction

**User Story:** As a creator, I want the system to analyze my platform habits, so that I can understand my engagement patterns.

#### Acceptance Criteria

1. WHEN video metadata is provided, THE System SHALL calculate call_to_action_freq
2. WHEN video metadata is provided, THE System SHALL identify upload_schedule patterns
3. WHEN video metadata is provided, THE System SHALL classify community_tone
4. THE System SHALL store all behavioral metrics in structured format

### Requirement 6: Baseline Persona Generation

**User Story:** As a creator, I want the system to create my baseline persona, so that I have a mathematical definition of my style.

#### Acceptance Criteria

1. WHEN all DNA extraction is complete, THE Encoder SHALL normalize extracted data across all four pillars
2. WHEN normalizing data, THE Encoder SHALL calculate the average of the top 10 performing videos as the gold standard
3. WHEN normalization is complete, THE Encoder SHALL generate a persona.json file containing the Baseline_Persona
4. THE persona.json file SHALL be valid JSON and conform to the Persona_Schema structure
5. WHEN a creator has fewer than 10 videos, THE Encoder SHALL use all available videos for baseline calculation

### Requirement 7: Drift Detection

**User Story:** As a creator, I want to compare new videos against my baseline, so that I can detect when I'm drifting from my authentic style.

#### Acceptance Criteria

1. WHEN a new video is analyzed, THE System SHALL compare its attributes against the Baseline_Persona
2. WHEN comparing attributes, THE System SHALL calculate a Drift_Score for each DNA_Pillar
3. WHEN Drift_Score exceeds a threshold, THE System SHALL generate an alert with specific drift details
4. WHEN generating alerts, THE System SHALL identify which specific attributes have changed
5. THE System SHALL display drift trends over time using rolling averages
6. WHEN displaying drift analysis, THE System SHALL correlate drift with performance metrics

### Requirement 8: Persona Injection

**User Story:** As a creator, I want to rewrite generic content using my style, so that all my content maintains my authentic voice.

#### Acceptance Criteria

1. WHEN a Creator provides generic text content, THE System SHALL rewrite it using the creator's Semantic DNA
2. WHEN rewriting content, THE System SHALL incorporate the creator's catchphrases
3. WHEN rewriting content, THE System SHALL match the creator's hook_style
4. WHEN rewriting content, THE System SHALL maintain the creator's sentiment patterns
5. THE System SHALL generate content that aligns with the creator's narrative_structure

### Requirement 9: Platform Adaptation

**User Story:** As a creator, I want to adapt my content for different platforms, so that I can maintain my identity across all channels.

#### Acceptance Criteria

1. WHEN a Creator requests platform adaptation, THE System SHALL accept the target platform as input
2. WHEN adapting for a target platform, THE System SHALL apply platform-specific constraints
3. WHEN adapting content, THE System SHALL preserve the creator's core identity attributes
4. WHEN adapting for short-form platforms, THE System SHALL compress pacing while maintaining visual and audio DNA
5. THE System SHALL generate adapted content that maintains the creator's Drift_Score within acceptable thresholds

### Requirement 10: Multi-Creator Management

**User Story:** As an agency, I want to monitor multiple creators simultaneously, so that I can identify drift across my client portfolio.

#### Acceptance Criteria

1. WHEN an Agency user logs in, THE System SHALL display a dashboard with all managed creators
2. WHEN displaying the dashboard, THE System SHALL show the current Drift_Score for each creator
3. WHEN a creator's Drift_Score exceeds a threshold, THE System SHALL highlight that creator with an alert
4. THE System SHALL allow filtering and sorting creators by Drift_Score
5. THE System SHALL provide aggregate analytics across all managed creators

### Requirement 11: Persona Schema Storage and Retrieval

**User Story:** As a developer, I want to store and retrieve persona schemas, so that the system can persist creator identities.

#### Acceptance Criteria

1. WHEN a Baseline_Persona is generated, THE System SHALL store it as a persona.json file
2. WHEN storing persona.json, THE System SHALL validate it against the Persona_Schema structure
3. WHEN a Creator requests their persona, THE System SHALL retrieve and return the persona.json file
4. THE System SHALL support versioning of persona.json files to track schema evolution
5. WHEN retrieving persona.json, THE System SHALL handle missing or corrupted files gracefully

### Requirement 12: Performance Correlation Analysis

**User Story:** As a creator, I want to see how style changes correlate with performance, so that I can make data-driven content decisions.

#### Acceptance Criteria

1. WHEN displaying drift analysis, THE System SHALL retrieve performance metrics for each video
2. WHEN performance metrics are available, THE System SHALL calculate correlation between drift and performance
3. WHEN correlation is significant, THE System SHALL highlight the relationship in the dashboard
4. THE System SHALL display which specific attribute changes correlate with performance drops
5. THE System SHALL provide recommendations based on correlation analysis

### Requirement 13: Schema Comparison

**User Story:** As an aspiring creator, I want to compare my content against successful creators, so that I can learn from their patterns.

#### Acceptance Criteria

1. WHEN a Creator requests schema comparison, THE System SHALL accept a target creator's schema as input
2. WHEN comparing schemas, THE System SHALL calculate differences across all four DNA pillars
3. WHEN displaying comparison results, THE System SHALL highlight the largest deviations
4. THE System SHALL provide specific recommendations for aligning with the target schema
5. THE System SHALL display side-by-side visualizations of both schemas

### Requirement 14: Authentication and Authorization

**User Story:** As a user, I want secure access to the platform, so that my persona data remains private.

#### Acceptance Criteria

1. WHEN a user attempts to access the System, THE System SHALL require authentication
2. WHEN a user authenticates, THE System SHALL verify their credentials
3. WHEN authentication fails, THE System SHALL return an error and deny access
4. THE System SHALL enforce role-based access control for Creator and Agency roles
5. WHEN a user accesses persona data, THE System SHALL verify they have authorization for that specific persona

### Requirement 15: Error Handling and Validation

**User Story:** As a user, I want clear error messages, so that I can understand and resolve issues.

#### Acceptance Criteria

1. WHEN invalid input is provided, THE System SHALL return a descriptive error message
2. WHEN video processing fails, THE System SHALL log the error and notify the user
3. WHEN API rate limits are exceeded, THE System SHALL queue requests and notify the user
4. THE System SHALL validate all input data before processing
5. WHEN validation fails, THE System SHALL specify which fields are invalid and why

### Requirement 16: Scalable Video Processing

**User Story:** As a system architect, I want robust video processing for large files, so that the system handles videos of any size without timeout issues.

#### Acceptance Criteria

1. WHEN processing large video files (1GB+, 15+ minutes), THE System SHALL use AWS Elemental MediaConvert for audio extraction and frame generation
2. WHEN MediaConvert processing completes, THE System SHALL store audio and frames directly in S3
3. WHEN video processing is initiated, THE System SHALL monitor MediaConvert job status via CloudWatch Events
4. THE System SHALL handle videos of any duration without Lambda timeout limitations
5. WHEN MediaConvert job fails, THE System SHALL log the error and notify the user

### Requirement 17: Heavy Dependency Management

**User Story:** As a developer, I want to deploy ML libraries without size constraints, so that Vision Bot and Audio Bot can use OpenCV and Librosa effectively.

#### Acceptance Criteria

1. WHEN deploying Vision_Bot, THE System SHALL use Docker Container Images stored in Amazon ECR
2. WHEN deploying Audio_Bot, THE System SHALL use Docker Container Images stored in Amazon ECR
3. THE Docker Container Images SHALL support up to 10GB of dependencies
4. WHEN Lambda functions execute, THE System SHALL load all required ML libraries from the container image
5. THE System SHALL handle container image updates and versioning

### Requirement 18: Token Cost Optimization

**User Story:** As a system architect, I want to minimize AI token costs, so that semantic analysis remains cost-effective at scale.

#### Acceptance Criteria

1. WHEN analyzing long transcripts, THE Text_Bot SHALL implement a two-stage summarization chain
2. WHEN summarizing transcripts, THE System SHALL use a cheaper model (Claude Haiku or Amazon Titan) for initial cleaning and summarization
3. WHEN performing deep analysis, THE System SHALL use Claude 3.5 Sonnet on the structured summary
4. THE summarization chain SHALL reduce token costs while maintaining analysis quality
5. WHEN summarization fails, THE System SHALL fall back to direct analysis with the primary model

### Requirement 19: Indian Context Authenticity Metrics

**User Story:** As an Indian creator, I want the system to measure cultural authenticity and relatability, so that I can understand my connection with local audiences.

#### Acceptance Criteria

1. WHEN analyzing content, THE System SHALL calculate a desi_meter score (0-1) for cultural authenticity
2. WHEN analyzing transcripts, THE System SHALL measure hinglish_frequency and switches_per_minute
3. WHEN analyzing visual content, THE System SHALL measure background_clutter as an authenticity indicator
4. WHEN calculating jugaad_score, THE System SHALL combine high visual chaos with good audio quality to identify authentic high-potential creators
5. WHEN analyzing semantic content, THE System SHALL identify cultural_markers, local_references, and relatable_examples
6. THE System SHALL store all Indian context metrics in the persona schema
7. WHEN detecting drift, THE System SHALL track changes in Indian context authenticity metrics
