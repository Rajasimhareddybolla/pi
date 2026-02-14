# Requirements Document: Project Mirror - Digital Persona Schema System

## 1. Feature Overview

Project Mirror is an Identity Preservation Engine designed to help YouTube content creators understand, maintain, and scale their unique creative voice. The system analyzes a creator's existing content to build a mathematical representation of their style—a "digital persona"—then provides tools to maintain consistency, detect drift, and adapt content across platforms while preserving authenticity.

### The Problem We're Solving

Content creators face a fundamental challenge: as they scale their content production, they struggle to maintain the authentic voice that made them successful. They spend hours manually analyzing what works, creating clips, studying trends, and adapting content for different platforms—all while trying not to lose their unique identity.

### Our Solution

We automate the tedious work of content analysis and provide creators with:
- Automated clip generation from long-form videos
- Data-driven insights into what makes their content successful
- Trend recommendations personalized to their style 
- Tools to learn from successful creators
- Platform-specific content adaptation that preserves their voice

### Target Users

1. **Content Creators**: Individual YouTubers who want to scale their content production while maintaining authenticity
2. **Agencies**: Content management agencies overseeing multiple creators who need to monitor consistency and performance
3. **Aspiring Creators**: New content creators who want to learn from successful creators in their niche

---

## 2. User Stories and Use Cases

### 2.0 User Stories (Quick Reference)

**US-1: Automated Clip Generation**
As a content creator who repurposes long-form videos into short clips, I want the system to automatically identify and suggest 5-10 high-potential clip moments from my videos, so that I can reduce clip creation time from 1+ hour to 5-10 minutes while maintaining my authentic style.

**US-2: Video Analysis and Feedback**
As a content creator seeking to improve my content, I want timestamp-level recommendations and analytics-driven insights through a conversational interface, so that I can understand exactly what works and what doesn't without spending 30-40 minutes consulting other creators or manually analyzing competitor videos.

**US-3: Trending Topic Recommendations**
As a content creator looking for my next video idea, I want personalized trending topic recommendations that blend current trends with my unique persona, so that I can stay relevant while maintaining authenticity and reduce decision paralysis when choosing topics.

**US-4: Creator Persona Cloning**
As an aspiring content creator, I want to analyze successful creators' personas and understand their content evolution journey, so that I can learn proven patterns and save 10+ hours of manual analysis while developing my own style.

**US-5: Drift Detection and Consistency Monitoring**
As an established content creator (or agency managing multiple creators), I want automatic alerts when my content drifts from my successful baseline style, so that I can catch consistency issues before they impact performance and maintain the authentic voice that made me successful.

**US-6: Platform-Specific Content Adaptation**
As a content creator who publishes across multiple platforms, I want my content automatically adapted to meet platform-specific constraints (duration, aspect ratio, pacing) while preserving my core identity, so that I can reduce adaptation time from 30-45 minutes to 5-10 minutes per platform.

**US-7: Persona-Based Content Generation**
As a content creator scaling my production, I want to rewrite generic content using my unique semantic DNA (catchphrases, hooks, narrative style), so that all my content maintains consistency and authenticity even when produced at scale.

**US-8: Multi-Language Content Adaptation**
As a content creator targeting regional audiences, I want vernacular translations (Hindi, Tamil, Telugu, etc.) that preserve my personality traits and humor, so that I can reach diverse audiences without losing my authentic voice.

**US-9: Performance-Correlated Insights**
As a content creator analyzing performance drops, I want to see which specific style changes correlate with performance metrics, so that I can make data-driven decisions about what to adjust rather than guessing.

**US-10: Agency Dashboard for Multi-Creator Management**
As a content agency managing multiple creators, I want a centralized dashboard showing drift sco res and consistency metrics for all creators, so that I can proactively maintain brand consistency and identify issues before they impact performance.

---

### 2.1 Automated Clip Generation

**User**: Short-form content creators who repurpose long-form videos into clips

**Current Pain Points**:
- Manually watching entire videos to identify clippable moments (1+ hour per video)
- Analyzing previous metrics to understand what performs well
- Editing and exporting multiple clip variations
- Guessing which moments will resonate with audiences

**What We're Solving**: The generic, tedious task of creating clips manually through hours of watching, analyzing, and editing

**How We Make Life Easier**:
- Automatically analyze long-form videos to identify high-potential clip moments
- Use the creator's persona to understand their typical viral patterns
- Leverage analytics from existing content to make informed decisions
- Generate multiple curated clip options with timestamps and context

**Expected Outcomes**:
- Reduce clip creation time from 1+ hour to 5-10 minutes of selection
- Increase clip success rate through data-driven moment selection
- Generate 5-10 curated clip options per long-form video
- Maintain creator's authentic style in every clip

**Success Metrics**:
- Time savings: 50-55 minutes per video (85-90% reduction)
- Clip selection accuracy: 70%+ of suggested clips meet creator approval
- Viral potential: Suggested clips should match or exceed creator's average clip performance

---

### 2.2 Video Analysis and Feedback

**User**: Content creators seeking actionable insights to improve their content

**Current Pain Points**:
- Lack of clear insights into what works and what doesn't in their videos
- No timestamp-level feedback on specific moments that need improvement
- Relying on experienced creators for feedback (time-consuming, inconsistent)
- Copying what worked for others without understanding why
- Watching competitors' videos manually to extract learnings

**What We're Solving**: The gap between creating content and understanding how to improve it systematically

**How We Make Life Easier**:
- Provide video-level and timestamp-level recommendations through conversational chat
- Enable 1-on-1 interactive analysis by simply pasting a URL or uploading a video
- Deliver analytics-driven insights without requiring technical expertise
- Compare performance against the creator's own baseline persona

**Expected Outcomes**:
- Meaningful, actionable insights that creators can immediately apply
- Specific recommendations tied to timestamps (e.g., "At 2:35, your pacing slowed by 30%")
- Data-backed suggestions rather than subjective opinions
- Clear understanding of which elements drive engagement

**Success Metrics**:
- Time savings: 30-40 minutes per video analysis (no need to consult others or watch competitor videos)
- Insight actionability: 80%+ of recommendations should be implementable
- Improvement correlation: Videos implementing suggestions should show measurable performance gains

---

### 2.3 Trending Topic Recommendations

**User**: Content creators looking for their next video idea

**Current Pain Points**:
- Manually browsing trending topics across platforms
- Uncertainty about which trends align with their style
- Risk of chasing trends that don't fit their persona
- Balancing trend exploitation vs. personal brand consistency

**What We're Solving**: The challenge of finding trending topics that authentically fit the creator's voice

**How We Make Life Easier**:
- Automatically surface trending topics from across the internet
- Blend trending topics with the creator's persona preferences
- Provide an exploration/exploitation slider (new topics vs. proven topics)
- Show personalized recommendations that match their style

**Expected Outcomes**:
- Curated list of trending topics ranked by fit with creator's persona
- Confidence scores for each recommendation
- Balance between staying relevant and staying authentic
- Reduced decision paralysis when choosing next video topic

**Success Metrics**:
- Recommendation relevance: 70%+ of suggested topics should interest the creator
- Topic-persona fit: Recommended topics should align with creator's semantic DNA
- Adoption rate: 40%+ of creators should act on at least one recommendation per week

---

### 2.4 Creator Persona Cloning

**User**: New or aspiring content creators who want to learn from successful creators

**Current Pain Points**:
- Manually analyzing what worked for successful creators
- Trying to imitate without understanding the underlying patterns
- Spending hours studying a creator's journey and evolution
- Guessing which elements of their style to adopt

**What We're Solving**: The time-intensive process of learning from successful creators through manual analysis

**How We Make Life Easier**:
- Create detailed personas of top YouTubers in any niche
- Extract their content journey and evolution over time
- Provide a clear roadmap of how they achieved success
- Recommend specific creators to emulate based on user's goals

**Expected Outcomes**:
- Comprehensive persona profiles of successful creators
- Timeline of their content evolution (what changed, when, and why)
- Actionable recommendations: "To become like [Creator], focus on these attributes"
- Script templates and style guides based on successful patterns

**Success Metrics**:
- Learning efficiency: Save 10+ hours of manual analysis per creator studied
- Pattern accuracy: Extracted personas should accurately represent creator's style
- Adoption success: New creators using cloned personas should see faster growth than control group

---

### 2.5 Drift Detection and Consistency Monitoring

**User**: Established creators and agencies managing multiple creators

**Current Pain Points**:
- Unintentionally drifting away from the style that made them successful
- No systematic way to monitor consistency across videos
- Discovering drift only after performance drops
- Agencies struggling to maintain brand consistency across multiple creators

**What We're Solving**: The invisible problem of style drift that erodes audience connection

**How We Make Life Easier**:
- Automatically compare each new video against the creator's baseline persona
- Calculate drift scores across visual, audio, semantic, and behavioral dimensions
- Generate alerts when drift exceeds acceptable thresholds
- Correlate drift with performance metrics to identify harmful changes

**Expected Outcomes**:
- Early warning system before performance drops
- Specific identification of what changed (e.g., "Your pacing slowed by 26%")
- Recommendations to realign with successful baseline
- Agency dashboard showing drift across all managed creators

**Success Metrics**:
- Early detection: Identify drift before 20% performance drop
- Alert accuracy: 80%+ of high-drift alerts should correlate with performance issues
- Recovery effectiveness: Creators acting on drift alerts should recover performance within 2-3 videos

---

### 2.6 Platform-Specific Content Adaptation

**User**: Creators who want to repurpose content across multiple platforms (YouTube, Instagram, TikTok, etc.)

**Current Pain Points**:
- Each platform has different constraints (duration, aspect ratio, pacing)
- Manually adapting content for each platform is time-consuming
- Risk of losing authentic voice when adapting to platform norms
- Uncertainty about which elements to preserve vs. adapt

**What We're Solving**: The challenge of maintaining identity while meeting platform-specific requirements

**How We Make Life Easier**:
- Automatically adapt content to meet platform constraints
- Preserve core identity attributes during adaptation
- Optimize for platform algorithms while staying authentic
- Generate vernacular translations for regional audiences

**Expected Outcomes**:
- Platform-optimized content that still feels authentic
- Automated adaptation reducing manual editing time
- Consistent brand voice across all platforms
- Regional language versions maintaining personality traits

**Success Metrics**:
- Adaptation time: Reduce from 30-45 minutes to 5-10 minutes per platform
- Identity preservation: Adapted content should maintain 80%+ persona alignment
- Cross-platform performance: Adapted content should match or exceed platform-specific benchmarks

---

## 3. Acceptance Criteria

### 3.1 Video Ingestion and Processing

**1.1** The system must successfully retrieve videos from YouTube channels using valid channel handles

**1.2** The system must decompose each video into three components: audio stream, visual frames (1fps), and transcript with speaker identification

**1.3** The system must provide clear error messages when video retrieval fails, including the reason for failure (private video, unavailable, rate limit, etc.)

**1.4** The system must handle batch ingestion of up to 50 videos per request without timeout

**1.5** The system must support common video formats (MP4, WebM, MOV) and resolutions up to 4K

**1.6** The system must complete video processing within 2x the video duration (e.g., 10-minute video processed in 20 minutes)

---

### 3.2 Visual DNA Extraction

**2.1** The system must calculate cut rate per minute (cuts/min) for any video with accuracy within ±10%

**2.2** The system must extract a color palette with 3-5 dominant colors and their hex codes

**2.3** The system must classify camera angles into categories (close-up, medium, wide) with distribution percentages

**2.4** The system must measure face presence as a ratio (0-1) indicating percentage of frames with faces

**2.5** The system must calculate average shot length in seconds

**2.6** The system must output structured JSON data for all visual metrics

**2.7** The system must measure visual density (sensory load) calibrated for Indian audience preferences

**2.8** The system must calculate background clutter score (0-1) as an authenticity indicator

**2.9** The system must compute jugaad score combining visual chaos and audio quality

---

### 3.3 Audio DNA Extraction

**3.1** The system must calculate average words per minute (WPM) from transcript and audio alignment

**3.2** The system must measure pitch variance across the audio stream

**3.3** The system must identify music genres present in the audio (if any)

**3.4** The system must detect silence gaps and calculate average gap duration and frequency

**3.5** The system must output structured JSON data for all audio metrics

**3.6** The system must measure auditory density (sensory load) for Indian audience preferences

**3.7** The system must assess audio quality (0-1) as a production value indicator

---

### 3.4 Semantic DNA Extraction

**4.1** The system must identify catchphrases that appear in 40%+ of videos with frequency scores

**4.2** The system must classify the creator's hook style (rhetorical question, bold claim, story opening, etc.)

**4.3** The system must extract topic clusters with weights indicating content focus distribution

**4.4** The system must measure sentiment (valence and arousal) across content

**4.5** The system must identify narrative structure patterns (problem-solution, tutorial, storytelling, etc.)

**4.6** The system must output structured JSON data for all semantic attributes

**4.7** The system must calculate "Desi-Meter" score (0-1) measuring Indian cultural authenticity

**4.8** The system must measure Hinglish code-mixing frequency (switches per minute)

**4.9** The system must identify cultural markers, local references, and relatable examples

---

### 3.5 Behavioral DNA Extraction

**5.1** The system must calculate call-to-action frequency from video descriptions and end screens

**5.2** The system must identify upload schedule patterns (frequency, preferred days, preferred times)

**5.3** The system must classify community tone (friendly-casual, professional, energetic, etc.)

**5.4** The system must output structured JSON data for all behavioral metrics

---

### 3.6 Persona Generation and Storage

**6.1** The system must aggregate DNA data across all analyzed videos, calculating mean and standard deviation for numeric attributes

**6.2** The system must calculate baseline metrics using only the top 10 performing videos (or all if fewer than 10)

**6.3** The system must generate a complete persona.json file containing all four DNA pillars (Visual, Audio, Semantic, Behavioral)

**6.4** The system must validate persona.json against the PersonaSchema before storage

**6.5** The system must store persona.json in S3 with versioning enabled

**6.6** The system must index persona vectors in Amazon OpenSearch for similarity search

**6.7** The system must include Indian context metrics (chaos score, desi-meter, jugaad score, hinglish metrics)

---

### 3.7 Drift Detection

**7.1** The system must analyze new videos and compare them against the baseline persona

**7.2** The system must calculate drift scores for each of the four DNA pillars (Visual, Audio, Semantic, Behavioral)

**7.3** The system must generate alerts when drift scores exceed configurable thresholds (default: 0.25)

**7.4** The system must identify specific attributes that changed and their deviation magnitude

**7.5** The system must track drift trends over time using rolling averages

**7.6** The system must correlate drift with performance metrics when available (views, retention, engagement)

**7.7** The system must use OpenSearch vector similarity for semantic drift detection

**7.8** The system must provide recommendations for realigning with baseline persona

---

### 3.8 Content Generation with Persona Injection

**8.1** The system must rewrite generic content using the creator's semantic DNA (catchphrases, hook style, narrative structure)

**8.2** The system must incorporate specific examples from past content using RAG (Retrieval-Augmented Generation)

**8.3** The system must maintain sentiment alignment within ±0.15 of baseline

**8.4** The system must preserve the core message while adjusting style

**8.5** The system must calculate alignment scores comparing generated content to persona

**8.6** The system must use Amazon Bedrock with Claude 3.5 Sonnet for content generation

**8.7** The system must leverage Knowledge Bases for Amazon Bedrock for RAG functionality

---

### 3.9 Platform Adaptation

**9.1** The system must adapt content to meet platform-specific constraints:
- YouTube Shorts: 60 seconds max, 9:16 aspect ratio
- Instagram Reels: 90 seconds max, 9:16 aspect ratio
- TikTok: 10 minutes max, 9:16 aspect ratio
- YouTube: No duration limit, 16:9 aspect ratio

**9.2** The system must adjust pacing and editing style for platform norms while preserving identity

**9.3** The system must validate that adapted content maintains 80%+ persona alignment

**9.4** The system must generate adaptation reports showing what was preserved and what was changed

**9.5** The system must support vernacular translation (Hindi, Tamil, Telugu, etc.) while preserving personality traits

---

### 3.10 Automated Clip Generation

**10.1** The system must analyze long-form videos to identify 5-10 high-potential clip moments

**10.2** The system must rank clip suggestions by viral potential based on:
- Persona alignment (does this moment match creator's successful patterns)
- Content density (information per second)
- Hook strength (first 3 seconds engagement potential)
- Emotional peaks (sentiment spikes)

**10.3** The system must provide timestamps and duration for each suggested clip

**10.4** The system must generate preview thumbnails for each clip suggestion

**10.5** The system must explain why each clip was suggested (e.g., "High energy moment matching your top-performing clips")

**10.6** The system must allow creators to adjust clip parameters (min/max duration, style preferences)

---

### 3.11 Video Analysis and Feedback

**11.1** The system must accept video input via URL or file upload

**11.2** The system must provide conversational, interactive analysis through chat interface

**11.3** The system must generate video-level insights (overall performance, strengths, weaknesses)

**11.4** The system must provide timestamp-level recommendations (e.g., "At 2:35, pacing slowed by 30%")

**11.5** The system must compare analyzed video against creator's baseline persona

**11.6** The system must identify specific improvements with actionable suggestions

**11.7** The system must explain recommendations in plain language without requiring technical expertise

---

### 3.12 Trending Topic Recommendations

**12.1** The system must retrieve trending topics from multiple sources (YouTube Trending, Google Trends, social media)

**12.2** The system must blend trending topics with creator's persona preferences

**12.3** The system must provide an exploration/exploitation slider:
- Exploitation (0.0): Only topics matching creator's proven style
- Balanced (0.5): Mix of familiar and new topics
- Exploration (1.0): Trending topics outside creator's usual content

**12.4** The system must rank recommendations by persona-fit score (0-1)

**12.5** The system must explain why each topic was recommended

**12.6** The system must refresh recommendations daily

---

### 3.13 Creator Persona Cloning

**13.1** The system must generate detailed personas for any public YouTube creator

**13.2** The system must extract the creator's content evolution timeline (how their style changed over time)

**13.3** The system must identify key success factors (what attributes correlate with their best-performing content)

**13.4** The system must provide actionable roadmap: "To become like [Creator], focus on these attributes"

**13.5** The system must generate script templates based on successful creator patterns

**13.6** The system must allow comparison between user's persona and target creator's persona

**13.7** The system must recommend specific creators to emulate based on user's goals and current style

---

### 3.14 Agency Dashboard

**14.1** The system must display all creators managed by an agency account

**14.2** The system must show current drift score for each creator

**14.3** The system must highlight creators with high drift (exceeding threshold)

**14.4** The system must allow filtering and sorting by drift score, performance, or last upload date

**14.5** The system must provide aggregate analytics across all managed creators

**14.6** The system must send notifications when any creator exceeds drift threshold

**14.7** The system must allow drill-down into individual creator drift reports

---

### 3.15 Authentication and Authorization

**15.1** The system must require authentication for all user-facing features

**15.2** The system must use Amazon Cognito for user authentication

**15.3** The system must support two user roles:
- Creator: Can manage their own persona and content
- Agency: Can manage multiple creator personas

**15.4** The system must enforce role-based access control (RBAC)

**15.5** The system must prevent users from accessing personas they don't own

**15.6** The system must support secure password requirements (min 8 characters, complexity rules)

**15.7** The system must implement token-based authentication with automatic refresh

---

### 3.16 Error Handling and Reliability

**16.1** The system must provide descriptive error messages for all failure scenarios

**16.2** The system must log all processing failures to CloudWatch with detailed error information

**16.3** The system must handle platform API rate limits gracefully by queuing requests

**16.4** The system must validate all input data before processing

**16.5** The system must reject invalid data with specific error messages indicating which fields are invalid

**16.6** The system must implement retry logic with exponential backoff for transient failures

**16.7** The system must preserve partial results when processing fails mid-pipeline

**16.8** The system must notify users when their processing jobs fail, with clear explanation

---

### 3.17 Performance and Scalability

**17.1** The system must process videos within 2x video duration (e.g., 10-min video in 20 minutes)

**17.2** The system must support concurrent processing of multiple videos per user

**17.3** The system must handle up to 100 concurrent users without degradation

**17.4** The system must respond to API requests within 2 seconds (excluding long-running jobs)

**17.5** The system must scale automatically based on load using AWS Lambda and Step Functions

**17.6** The system must optimize token costs using summarization chain (cheaper model for preprocessing, Claude 3.5 Sonnet for analysis)

---

### 3.18 Data Storage and Retrieval

**18.1** The system must store all videos in S3 with organized bucket structure

**18.2** The system must store persona.json files in S3 with versioning enabled

**18.3** The system must maintain version history for personas (minimum 10 versions)

**18.4** The system must index persona vectors in Amazon OpenSearch for similarity search

**18.5** The system must retrieve personas within 500ms

**18.6** The system must handle missing or corrupted persona files gracefully with clear error messages

**18.7** The system must implement S3 lifecycle policies for cost optimization

---

### 3.19 Indian Context Features

**19.1** The system must calculate "Desi-Meter" score measuring cultural authenticity (0-1 scale)

**19.2** The system must measure Hinglish code-mixing frequency (switches per minute)

**19.3** The system must identify cultural markers and local references

**19.4** The system must calculate "Chaos Engine" metrics (visual and auditory density)

**19.5** The system must compute "Jugaad Aesthetic" score (background clutter + audio quality)

**19.6** The system must support multi-language transcription (Hindi, English, Hinglish)

**19.7** The system must provide vernacular translation while preserving personality traits

---

### 3.20 Monitoring and Observability

**20.1** The system must log all operations to CloudWatch Logs

**20.2** The system must emit CloudWatch metrics for:
- Processing time per video
- Success/failure rates
- API latency
- Bedrock token usage
- OpenSearch query performance

**20.3** The system must set up CloudWatch alarms for critical failures

**20.4** The system must provide distributed tracing using AWS X-Ray

**20.5** The system must maintain audit logs for all user actions

---

## 4. Constraints and Assumptions

### 4.1 Technical Constraints

- The system must be built on AWS infrastructure using serverless architecture
- The system must use Amazon Bedrock with multi modality models for AI analysis
- The system must use Amazon Transcribe for multi-language audio transcription
- The system must use Amazon OpenSearch Serverless for vector storage
- The system must use AWS Lambda for compute (with Docker containers for heavy ML libraries)
- The system must use AWS Step Functions for orchestration
- The system must use AWS Elemental MediaConvert for video processing (to avoid Lambda timeout issues)
- The system must support videos up to 2 hours in duration
- The system must handle video files up to 2GB in size

### 4.2 Business Constraints

- The system must optimize for cost-efficiency using serverless architecture
- The system must minimize Bedrock token costs using summarization chain
- The system must comply with YouTube Terms of Service for video retrieval
- The system must respect platform API rate limits
- The system must not store copyrighted content beyond processing requirements

### 4.3 Assumptions

- Users have valid YouTube channel handles or video URLs
- Videos are publicly accessible (not private or region-locked)
- Users consent to analysis of their content
- Performance metrics (views, retention, engagement) are available via platform APIs
- Users understand that persona accuracy improves with more videos analyzed (minimum 10 videos recommended)
- Indian context features are calibrated for Hindi/English content (other languages may have reduced accuracy)
- Users have basic understanding of content creation concepts (hooks, pacing, engagement)

---

## 5. Success Criteria

### 5.1 User Satisfaction

- 80%+ of users report that persona accurately represents their style
- 75%+ of users find drift alerts actionable and helpful
- 70%+ of users adopt at least one recommendation per week
- 85%+ of users report time savings compared to manual analysis

### 5.2 System Performance

- 95%+ uptime for all services
- 90%+ success rate for video processing
- <2 second API response time for non-processing requests
- Processing time within 2x video duration for 95% of videos

### 5.3 Business Impact

- Clip generation time reduced by 85%+ (from 60+ minutes to <10 minutes)
- Video analysis time reduced by 75%+ (from 40 minutes to <10 minutes)
- Creator learning time reduced by 90%+ (from 10+ hours to <1 hour per creator studied)
- Early drift detection preventing 50%+ of performance drops

---

## 6. Out of Scope (Future Enhancements)

The following features are explicitly out of scope for the initial release but may be considered for future iterations:

- Real-time video streaming analysis
- Live stream persona tracking
- Automated video editing and rendering
- Direct platform publishing integration
- Collaborative features for team-based content creation
- Advanced A/B testing for content variations
- Predictive analytics for video performance forecasting
- Integration with non-YouTube platforms (TikTok, Instagram) for ingestion
- Mobile application (initial release is web-only)
- Multi-creator collaboration tools
- Automated thumbnail generation
- Voice cloning for dubbing
- Advanced video effects and transitions

---

## 7. Glossary

**Persona**: A mathematical representation of a creator's unique style across four DNA pillars (Visual, Audio, Semantic, Behavioral)

**DNA Pillar**: One of four dimensions used to characterize content: Visual (editing style), Audio (sound characteristics), Semantic (language and meaning), Behavioral (patterns and habits)

**Drift**: The degree to which new content deviates from a creator's baseline persona

**Baseline Persona**: The canonical representation of a creator's style, calculated from their top-performing videos

**Desi-Meter**: A metric measuring Indian cultural authenticity and relatability (0-1 scale)

**Chaos Engine**: A metric measuring sensory load (visual and auditory density) calibrated for Indian audience preferences

**Jugaad Aesthetic**: A metric combining background clutter and audio quality to identify authentic Indian creator style

**Hinglish**: Code-mixing between Hindi and English, common in Indian content

**RAG (Retrieval-Augmented Generation)**: A technique that retrieves relevant past examples to inform content generation

**Persona Injection**: The process of rewriting content to match a creator's semantic DNA

**Platform Polymorph**: Adapting content for different platforms while preserving core identity

---

*This requirements document serves as the foundation for the Project Mirror system. All design decisions, implementation tasks, and testing strategies should trace back to these requirements.*
