# Implementation Plan: Project Mirror - Digital Persona Schema System

## Overview

This implementation plan breaks down Project Mirror into discrete, incremental coding tasks following the updated AWS-native serverless architecture. The system will be built in phases: (1) AWS infrastructure and core data models, (2) Video processing with MediaConvert, (3) Extraction pipeline with Docker-based Lambda functions, (4) Encoding with token optimization, (5) Application layer with Indian context features, and (6) API and authentication. Each task builds on previous work, with property-based tests integrated throughout.

Implementation language: **Python** (using AWS SDK (boto3), FastAPI for API, Hypothesis for property testing, OpenCV for vision, Librosa for audio, and Amazon Bedrock for semantic analysis)

## Tasks

- [ ] 1. Set up AWS infrastructure and core data models
  - Create Python project with virtual environment and AWS SDK
  - Set up FastAPI application skeleton
  - Define PersonaSchema, VisualDNA, AudioDNA, SemanticDNA, BehavioralDNA as Pydantic models
  - Add new fields: background_clutter, jugaad_score, audio_quality, desi_meter, hinglish_metrics
  - Implement JSON schema validation for persona.json
  - Set up testing framework (pytest + Hypothesis)
  - Configure AWS credentials and region settings
  - _Requirements: 6.4, 11.2, 19.6_

- [ ]* 1.1 Write property test for persona schema validation
  - **Property 13: Persona Schema Round-Trip**
  - **Validates: Requirements 6.4, 11.2**

- [ ] 2. Set up AWS S3 storage infrastructure
  - [ ] 2.1 Create S3Service class for storage operations
    - Implement bucket creation with lifecycle policies
    - Implement atomic file uploads with versioning
    - Implement file retrieval with error handling
    - Implement presigned URL generation for secure access
    - _Requirements: 11.1, 11.3, 11.4_

  - [ ]* 2.2 Write property test for S3 storage round-trip
    - **Property 25: Persona Storage Round-Trip**
    - **Validates: Requirements 11.1, 11.3**

  - [ ]* 2.3 Write property test for S3 versioning
    - **Property 26: Persona Versioning**
    - **Validates: Requirements 11.4**

  - [ ]* 2.4 Write property test for graceful S3 error handling
    - **Property 27: Graceful File Handling**
    - **Validates: Requirements 11.5**

- [ ] 3. Set up Amazon OpenSearch Serverless for vector storage
  - [ ] 3.1 Create OpenSearchService class
    - Implement collection creation with vector index configuration
    - Implement persona vector indexing with embeddings
    - Implement vector similarity search for drift detection
    - Implement query optimization for performance
    - _Requirements: 7.1, 7.5_

  - [ ]* 3.2 Write unit tests for OpenSearch operations
    - Test vector indexing and retrieval
    - Test similarity search accuracy
    - Test error handling for connection failures
    - _Requirements: 7.1_

- [ ] 4. Implement video ingestion service with Step Functions
  - [ ] 4.1 Create VideoIngestionService Lambda function
    - Implement YouTube API integration for video retrieval
    - Implement channel handle validation
    - Implement video download with retry logic
    - Handle rate limiting with exponential backoff
    - Trigger Step Functions state machine for processing
    - _Requirements: 1.1, 1.3, 15.3_

  - [ ]* 4.2 Write property test for video retrieval completeness
    - **Property 1: Video Retrieval Completeness**
    - **Validates: Requirements 1.1, 1.4**

  - [ ]* 4.3 Write property test for error message descriptiveness
    - **Property 3: Error Message Descriptiveness**
    - **Validates: Requirements 1.3, 15.1, 15.2**

  - [ ]* 4.4 Write unit tests for rate limit handling
    - Test queue behavior when limits exceeded
    - Test user notification via SNS
    - _Requirements: 15.3_

- [ ] 5. Implement AWS Elemental MediaConvert integration
  - [ ] 5.1 Create MediaConvertService class
    - Implement MediaConvert job creation for audio extraction
    - Implement MediaConvert job creation for frame generation (1fps)
    - Implement job status monitoring via CloudWatch Events
    - Implement error handling and retry logic
    - Configure output settings for optimal quality
    - _Requirements: 16.1, 16.2, 16.3, 16.4, 16.5_

  - [ ] 5.2 Create VideoSplitter Lambda function
    - Trigger MediaConvert jobs for video processing
    - Monitor MediaConvert job completion
    - Trigger Amazon Transcribe after MediaConvert completes
    - Handle multiple video formats
    - Store component paths in DynamoDB for tracking
    - _Requirements: 1.2, 1.5, 16.1_

  - [ ]* 5.3 Write property test for component separation
    - **Property 2: Video Component Separation**
    - **Validates: Requirements 1.2**

  - [ ]* 5.4 Write property test for format support
    - **Property 4: Format Support Universality**
    - **Validates: Requirements 1.5**

  - [ ]* 5.5 Write unit tests for MediaConvert integration
    - Test job creation with various video sizes
    - Test timeout handling for large files
    - Test error recovery
    - _Requirements: 16.1, 16.4_

- [ ] 6. Checkpoint - Ensure ingestion and MediaConvert pipeline works
  - Ensure all tests pass, ask the user if questions arise.

- [ ] 7. Set up Amazon ECR and Docker containers for ML Lambda functions
  - [ ] 7.1 Create Dockerfile for Vision Bot
    - Install OpenCV and computer vision dependencies
    - Configure Lambda runtime interface
    - Optimize image size and layers
    - _Requirements: 17.1, 17.3_

  - [ ] 7.2 Create Dockerfile for Audio Bot
    - Install Librosa and audio processing dependencies
    - Configure Lambda runtime interface
    - Optimize image size and layers
    - _Requirements: 17.2, 17.3_

  - [ ] 7.3 Set up ECR repositories and CI/CD
    - Create ECR repositories for both containers
    - Implement automated build and push pipeline
    - Configure Lambda to use container images
    - _Requirements: 17.1, 17.2, 17.5_

- [ ] 8. Implement Vision Bot with Indian context features
  - [ ] 8.1 Create VisionBot Lambda function (Docker-based)
    - Implement shot boundary detection using frame differencing
    - Implement cut_rate_per_min calculation
    - Implement color palette extraction using k-means clustering
    - Implement camera angle classification
    - Implement face detection and presence calculation
    - Implement avg_shot_length_sec calculation
    - Implement visual_density calculation for Chaos Engine
    - Implement background_clutter measurement for Jugaad Aesthetic
    - Implement jugaad_score calculation (high clutter + good quality)
    - _Requirements: 2.1, 2.2, 2.3, 2.4, 2.5, 2.6, 2.7, 2.8, 19.3, 19.4_

  - [ ]* 8.2 Write property test for Vision Bot output completeness
    - **Property 5: Vision Bot Output Completeness**
    - **Validates: Requirements 2.1, 2.2, 2.3, 2.4, 2.5, 2.6, 2.7, 2.8**

  - [ ]* 8.3 Write unit tests for edge cases
    - Test single frame input
    - Test frames with no faces
    - Test monochrome frames
    - Test high clutter backgrounds
    - _Requirements: 2.1-2.8, 19.3_

- [ ] 9. Implement Audio Bot with Indian context features
  - [ ] 9.1 Create AudioBot Lambda function (Docker-based)
    - Implement WPM calculation by aligning transcript with audio
    - Implement pitch variance measurement using pitch tracking
    - Implement music genre classification using pre-trained model
    - Implement silence gap detection using amplitude thresholds
    - Implement auditory_density calculation for Chaos Engine
    - Implement audio_quality measurement for Jugaad score
    - _Requirements: 3.1, 3.2, 3.3, 3.4, 3.5, 3.6, 19.4_

  - [ ]* 9.2 Write property test for Audio Bot output completeness
    - **Property 6: Audio Bot Output Completeness**
    - **Validates: Requirements 3.1, 3.2, 3.3, 3.4, 3.5, 3.6**

  - [ ]* 9.3 Write unit tests for edge cases
    - Test audio with no speech
    - Test pure silence
    - Test audio with no music
    - Test low vs high audio quality
    - _Requirements: 3.1-3.6, 19.4_

- [ ] 10. Implement Amazon Transcribe integration
  - [ ] 10.1 Create TranscribeService class
    - Implement multi-language transcription (Hindi/English)
    - Implement speaker identification
    - Implement job status monitoring
    - Handle transcription errors gracefully
    - _Requirements: 1.2_

  - [ ]* 10.2 Write unit tests for Transcribe integration
    - Test Hindi transcription
    - Test English transcription
    - Test Hinglish (code-mixed) transcription
    - Test speaker identification
    - _Requirements: 1.2_

- [ ] 11. Implement Text Bot with token optimization and Indian context features
  - [ ] 11.1 Create BedrockService class for AI operations
    - Implement Claude 3.5 Sonnet integration
    - Implement Claude Haiku integration for summarization
    - Implement Amazon Titan integration as fallback
    - Implement retry logic with exponential backoff
    - Handle throttling and quota limits
    - _Requirements: 18.1, 18.2, 18.3_

  - [ ] 11.2 Create TextBot Lambda function with summarization chain
    - Implement two-stage summarization (Haiku/Titan → Sonnet)
    - Implement catchphrase detection using n-gram frequency
    - Implement hook style classification using Bedrock
    - Implement topic clustering using embeddings
    - Implement sentiment analysis (valence and arousal)
    - Implement narrative structure pattern matching
    - Implement Desi-Meter calculation for cultural authenticity
    - Implement Hinglish tokenizer for code-mixing detection
    - Implement switches_per_minute calculation
    - Identify cultural_markers and local_references
    - _Requirements: 4.1, 4.2, 4.3, 4.4, 4.5, 4.6, 4.7, 4.8, 4.9, 18.1, 18.2, 18.3, 19.1, 19.2, 19.5_

  - [ ]* 11.3 Write property test for Text Bot output completeness
    - **Property 7: Text Bot Output Completeness**
    - **Validates: Requirements 4.1, 4.2, 4.3, 4.4, 4.5, 4.6, 4.7, 4.8, 4.9**

  - [ ]* 11.4 Write property test for token cost optimization
    - **Property 44: Token Cost Reduction**
    - **Validates: Requirements 18.4**

  - [ ]* 11.5 Write unit tests for edge cases
    - Test very short transcripts
    - Test pure Hindi transcripts
    - Test pure English transcripts
    - Test high Hinglish frequency
    - Test transcripts with cultural markers
    - _Requirements: 4.1-4.9, 19.1, 19.2_

- [ ] 12. Implement behavioral metadata extractor
  - [ ] 12.1 Create BehavioralExtractor Lambda function
    - Implement CTA frequency calculation from descriptions
    - Implement upload schedule pattern detection
    - Implement community tone classification
    - _Requirements: 5.1, 5.2, 5.3_

  - [ ]* 12.2 Write property test for behavioral metrics extraction
    - **Property 8: Behavioral Metrics Extraction**
    - **Validates: Requirements 5.1, 5.2, 5.3**

- [ ]* 13. Write property test for analyzer structured output
  - **Property 9: Analyzer Structured Output**
  - **Validates: Requirements 2.9, 3.7, 4.10, 5.4**

- [ ] 14. Checkpoint - Ensure all analyzers work with AWS services
  - Ensure all tests pass, ask the user if questions arise.

- [ ] 15. Implement normalizer with Indian context metrics
  - [ ] 15.1 Create Normalizer Lambda function
    - Implement statistical aggregation (mean, std_dev) for numeric attributes
    - Implement top-performer identification based on video metrics
    - Implement data normalization across scales
    - Handle missing data gracefully
    - Calculate aggregate Indian context metrics (chaos_score, jugaad_score, desi_meter)
    - Generate embeddings using Amazon Bedrock for OpenSearch
    - _Requirements: 6.1, 6.2, 19.6_

  - [ ]* 15.2 Write property test for DNA normalization
    - **Property 10: DNA Normalization Completeness**
    - **Validates: Requirements 6.1**

  - [ ]* 15.3 Write property test for top performer baseline
    - **Property 11: Top Performer Baseline Calculation**
    - **Validates: Requirements 6.2**

- [ ] 16. Implement baseline persona generator with OpenSearch indexing
  - [ ] 16.1 Create BaselinePersonaGenerator Lambda function
    - Implement persona.json construction from normalized data
    - Implement schema validation
    - Implement versioning metadata
    - Store persona.json in S3 with versioning
    - Index persona vectors in OpenSearch Serverless
    - _Requirements: 6.3, 6.4, 19.6_

  - [ ]* 16.2 Write property test for persona generation
    - **Property 12: Persona Generation Completeness**
    - **Validates: Requirements 6.3**

  - [ ]* 16.3 Write unit tests for OpenSearch indexing
    - Test vector embedding generation
    - Test index creation and updates
    - Test error handling
    - _Requirements: 6.3_

- [ ] 17. Implement drift detector with OpenSearch vector similarity
  - [ ] 17.1 Create DriftDetector Lambda function
    - Implement video analysis pipeline reuse for new videos
    - Implement per-attribute drift calculation using distance metrics
    - Implement vector similarity search in OpenSearch
    - Implement drift score calculation for each DNA pillar
    - Implement alert generation based on thresholds
    - Implement rolling average calculation for trends
    - Track Indian context drift (chaos_score, desi_meter, jugaad_score, hinglish_switches)
    - _Requirements: 7.1, 7.2, 7.3, 7.4, 7.5, 19.7_

  - [ ]* 17.2 Write property test for drift score calculation
    - **Property 14: Drift Score Calculation**
    - **Validates: Requirements 7.1, 7.2**

  - [ ]* 17.3 Write property test for drift alert generation
    - **Property 15: Drift Alert Generation**
    - **Validates: Requirements 7.3, 7.4**

  - [ ]* 17.4 Write property test for drift trend calculation
    - **Property 16: Drift Trend Calculation**
    - **Validates: Requirements 7.5**

  - [ ] 17.5 Implement performance correlation analysis
    - Retrieve performance metrics from video metadata
    - Calculate correlation between drift and performance
    - Identify attribute-performance relationships
    - Generate Bedrock-powered recommendations
    - _Requirements: 7.6, 12.1, 12.2, 12.4_

  - [ ]* 17.6 Write property test for performance correlation
    - **Property 17: Performance Correlation**
    - **Validates: Requirements 7.6, 12.2**

  - [ ]* 17.7 Write property test for attribute-performance correlation
    - **Property 30: Attribute-Performance Correlation**
    - **Validates: Requirements 12.4**

  - [ ]* 17.8 Write unit tests for drift detection scenarios
    - Test identical videos (zero drift)
    - Test completely different videos (high drift)
    - Test gradual drift over sequence
    - Test Indian context drift scenarios
    - _Requirements: 7.1-7.6, 19.7_

- [ ] 18. Implement persona injector with Knowledge Bases for Amazon Bedrock
  - [ ] 18.1 Set up Knowledge Bases for Amazon Bedrock
    - Create knowledge base with persona data
    - Configure vector store integration with OpenSearch
    - Implement RAG retrieval for past content examples
    - _Requirements: 8.1_

  - [ ] 18.2 Create PersonaInjector Lambda function
    - Implement Bedrock prompt construction with persona attributes
    - Implement RAG-based content rewriting using Knowledge Bases
    - Implement output validation against semantic DNA
    - Implement iterative refinement for low alignment
    - Preserve Indian context markers (Hinglish, cultural references)
    - _Requirements: 8.1, 8.2, 8.3, 8.4, 8.5_

  - [ ]* 18.3 Write property test for semantic DNA preservation
    - **Property 18: Semantic DNA Preservation in Rewrites**
    - **Validates: Requirements 8.1, 8.2, 8.3, 8.4, 8.5**

  - [ ]* 18.4 Write unit tests for rewrite scenarios
    - Test very short content
    - Test content with Hinglish
    - Test content with cultural references
    - Test different tones
    - _Requirements: 8.1-8.5_

- [ ] 19. Implement platform polymorph with vernacular translation
  - [ ] 19.1 Create PlatformPolymorph Lambda function
    - Define platform-specific constraints (TikTok, YouTube Shorts, Instagram)
    - Implement content adaptation logic using Bedrock
    - Implement identity preservation validation
    - Implement drift score checking for adapted content
    - Implement vernacular translation (Hindi, Tamil, Telugu) using Bedrock
    - Preserve personality traits and catchphrases in translations
    - _Requirements: 9.1, 9.2, 9.3, 9.4, 9.5_

  - [ ]* 19.2 Write property test for platform constraint application
    - **Property 19: Platform Constraint Application**
    - **Validates: Requirements 9.1, 9.2**

  - [ ]* 19.3 Write property test for identity preservation
    - **Property 20: Identity Preservation in Adaptation**
    - **Validates: Requirements 9.3, 9.4, 9.5**

  - [ ]* 19.4 Write unit tests for platform adaptations
    - Test TikTok adaptation
    - Test YouTube Shorts adaptation
    - Test Instagram Reels adaptation
    - Test vernacular translations
    - _Requirements: 9.1-9.5_

- [ ] 20. Checkpoint - Ensure application layer works with AWS services
  - Ensure all tests pass, ask the user if questions arise.

- [ ] 21. Implement schema comparison
  - [ ] 21.1 Create SchemaComparator Lambda function
    - Implement difference calculation across all DNA pillars
    - Implement deviation highlighting
    - Implement recommendation generation using Bedrock
    - Implement visualization data generation
    - Compare Indian context metrics between schemas
    - _Requirements: 13.1, 13.2, 13.3, 13.4, 13.5_

  - [ ]* 21.2 Write property test for schema comparison completeness
    - **Property 32: Schema Comparison Completeness**
    - **Validates: Requirements 13.1, 13.2**

  - [ ]* 21.3 Write property test for deviation highlighting
    - **Property 33: Deviation Highlighting**
    - **Validates: Requirements 13.3**

  - [ ]* 21.4 Write property test for comparison recommendations
    - **Property 34: Comparison Recommendations**
    - **Validates: Requirements 13.4**

  - [ ]* 21.5 Write property test for schema visualization
    - **Property 35: Schema Visualization**
    - **Validates: Requirements 13.5**

- [ ] 22. Implement recommendation engine
  - [ ] 22.1 Create RecommendationEngine Lambda function
    - Implement correlation-based recommendation generation
    - Implement recommendation prioritization
    - Implement recommendation formatting using Bedrock
    - Generate Indian context-specific recommendations
    - _Requirements: 12.3, 12.5_

  - [ ]* 22.2 Write property test for correlation highlighting
    - **Property 29: Correlation Highlighting**
    - **Validates: Requirements 12.3**

  - [ ]* 22.3 Write property test for correlation-based recommendations
    - **Property 31: Correlation-Based Recommendations**
    - **Validates: Requirements 12.5**

  - [ ]* 22.4 Write property test for performance metrics retrieval
    - **Property 28: Performance Metrics Retrieval**
    - **Validates: Requirements 12.1**

- [ ] 23. Implement agency dashboard backend
  - [ ] 23.1 Create AgencyDashboard Lambda function
    - Implement multi-creator data retrieval from S3 and OpenSearch
    - Implement drift score aggregation
    - Implement filtering and sorting logic
    - Implement aggregate analytics calculation
    - Display Indian context metrics across portfolio
    - _Requirements: 10.1, 10.2, 10.3, 10.4, 10.5_

  - [ ]* 23.2 Write property test for dashboard completeness
    - **Property 21: Agency Dashboard Completeness**
    - **Validates: Requirements 10.1, 10.2**

  - [ ]* 23.3 Write property test for high drift highlighting
    - **Property 22: High Drift Highlighting**
    - **Validates: Requirements 10.3**

  - [ ]* 23.4 Write property test for creator list operations
    - **Property 23: Creator List Operations**
    - **Validates: Requirements 10.4**

  - [ ]* 23.5 Write property test for aggregate analytics
    - **Property 24: Aggregate Analytics Calculation**
    - **Validates: Requirements 10.5**

- [ ] 24. Implement Amazon Cognito authentication
  - [ ] 24.1 Set up Cognito User Pool
    - Create user pool with email/password authentication
    - Configure user groups for Creator and Agency roles
    - Set up JWT token configuration
    - Configure MFA if needed
    - _Requirements: 14.1, 14.2, 14.4_

  - [ ] 24.2 Create AuthService class
    - Implement user authentication with Cognito
    - Implement JWT token verification
    - Implement role-based access control (Creator, Agency)
    - Implement persona-level authorization using IAM policies
    - _Requirements: 14.1, 14.2, 14.3, 14.4, 14.5_

  - [ ]* 24.3 Write property test for authentication requirement
    - **Property 36: Authentication Requirement**
    - **Validates: Requirements 14.1**

  - [ ]* 24.4 Write property test for credential verification
    - **Property 37: Credential Verification**
    - **Validates: Requirements 14.2**

  - [ ]* 24.5 Write property test for authentication failure handling
    - **Property 38: Authentication Failure Handling**
    - **Validates: Requirements 14.3**

  - [ ]* 24.6 Write property test for role-based access control
    - **Property 39: Role-Based Access Control**
    - **Validates: Requirements 14.4**

  - [ ]* 24.7 Write property test for persona authorization
    - **Property 40: Persona Authorization**
    - **Validates: Requirements 14.5**

- [ ] 25. Implement input validation and error handling
  - [ ] 25.1 Create ValidationService class
    - Implement input validation for all API endpoints
    - Implement descriptive error message generation
    - Implement CloudWatch logging for all errors
    - Implement SNS notifications for user alerts
    - _Requirements: 15.1, 15.2, 15.4, 15.5_

  - [ ]* 25.2 Write property test for input validation
    - **Property 41: Input Validation**
    - **Validates: Requirements 15.4, 15.5**

  - [ ]* 25.3 Write property test for processing failure logging
    - **Property 42: Processing Failure Logging**
    - **Validates: Requirements 15.2**

  - [ ]* 25.4 Write property test for rate limit handling
    - **Property 43: Rate Limit Handling**
    - **Validates: Requirements 15.3**

- [ ] 26. Implement API Gateway and REST API endpoints
  - [ ] 26.1 Set up API Gateway with Lambda integration
    - Configure REST API with proper CORS settings
    - Set up request/response transformations
    - Configure throttling and rate limiting
    - Set up CloudWatch logging
    - _Requirements: 15.3_

  - [ ] 26.2 Create API routes for video ingestion
    - POST /api/ingest - Start video ingestion job (triggers Step Functions)
    - GET /api/ingest/{job_id} - Get ingestion status
    - _Requirements: 1.1_

  - [ ] 26.3 Create API routes for persona management
    - GET /api/persona/{creator_id} - Get persona from S3
    - POST /api/persona/{creator_id}/generate - Generate baseline persona
    - _Requirements: 6.3, 11.3_

  - [ ] 26.4 Create API routes for drift detection
    - POST /api/drift/analyze - Analyze video for drift
    - GET /api/drift/trends/{creator_id} - Get drift trends from OpenSearch
    - _Requirements: 7.1, 7.5_

  - [ ] 26.5 Create API routes for persona injection
    - POST /api/inject - Rewrite content using persona with RAG
    - _Requirements: 8.1_

  - [ ] 26.6 Create API routes for platform adaptation
    - POST /api/adapt - Adapt content for platform
    - POST /api/translate - Translate to vernacular language
    - _Requirements: 9.1_

  - [ ] 26.7 Create API routes for schema comparison
    - POST /api/compare - Compare two schemas
    - _Requirements: 13.1_

  - [ ] 26.8 Create API routes for agency dashboard
    - GET /api/agency/dashboard - Get dashboard data
    - GET /api/agency/creators - Get filtered/sorted creator list
    - _Requirements: 10.1, 10.4_

  - [ ] 26.9 Add Cognito authorizer to all routes
    - Implement JWT verification middleware
    - Implement authorization checks based on user role
    - _Requirements: 14.1, 14.5_

- [ ] 27. Implement Step Functions orchestration
  - [ ] 27.1 Create Step Functions state machine for video processing
    - Define states for ingestion → MediaConvert → Transcribe → Analyze → Encode
    - Implement parallel execution for Vision/Audio/Text bots
    - Implement error handling and retry logic
    - Implement timeout handling
    - Configure CloudWatch Events for monitoring
    - _Requirements: 1.1, 1.2, 16.3_

  - [ ]* 27.2 Write integration tests for Step Functions workflow
    - Test complete pipeline execution
    - Test error recovery
    - Test parallel execution
    - _Requirements: 1.1, 1.2_

- [ ] 28. Set up CloudWatch monitoring and alarms
  - [ ] 28.1 Create CloudWatch dashboards
    - Dashboard for ingestion pipeline metrics
    - Dashboard for Lambda execution metrics
    - Dashboard for Bedrock API usage and costs
    - Dashboard for OpenSearch performance
    - Dashboard for MediaConvert job status
    - _Requirements: 15.2_

  - [ ] 28.2 Configure CloudWatch alarms
    - Alarm for high Lambda error rates
    - Alarm for Bedrock throttling
    - Alarm for OpenSearch failures
    - Alarm for MediaConvert job failures
    - Alarm for high drift scores
    - _Requirements: 15.2_

- [ ]* 29. Write integration tests for complete workflows
  - Test complete ingestion → MediaConvert → Transcribe → analyze → baseline generation flow
  - Test drift detection with real video sequence and OpenSearch
  - Test persona injection with Knowledge Bases RAG
  - Test agency dashboard with multiple creators
  - Test Indian context feature calculations end-to-end
  - Test token cost optimization in Text Bot
  - _Requirements: All_

- [ ] 30. Final checkpoint - Ensure all tests pass and AWS services are integrated
  - Run full test suite
  - Verify all property tests pass with 100+ iterations
  - Verify all unit tests pass
  - Verify integration tests pass
  - Verify AWS service integrations work correctly
  - Test Docker container deployments
  - Test MediaConvert processing with large files
  - Test Bedrock token optimization
  - Test Indian context metrics accuracy
  - Ask the user if questions arise

## Notes

- Tasks marked with `*` are optional and can be skipped for faster MVP
- Each task references specific requirements for traceability
- Property tests validate universal correctness properties with 100+ iterations
- Unit tests validate specific examples and edge cases
- Checkpoints ensure incremental validation throughout development
- All property tests must include comment tags: `# Feature: project-mirror, Property {N}: {description}`
- AWS services used: S3, Lambda (with Docker containers), Step Functions, MediaConvert, Transcribe, Bedrock, OpenSearch Serverless, Cognito, API Gateway, CloudWatch, ECR, SNS, SQS
- Docker containers enable heavy ML libraries (OpenCV, Librosa) without Lambda size limits
- MediaConvert handles large video processing without Lambda timeout issues
- Two-stage summarization chain reduces Bedrock token costs
- Indian context features (Desi-Meter, Hinglish, Jugaad) are integrated throughout the pipeline
