name: "Multi-Language Video Streaming Platform - Netflix-Like Architecture"
description: |

## Purpose
Build a production-ready multi-language video streaming platform similar to Netflix using modern microservices architecture with Bun, ElysiaJS, Go, Rust, RabbitMQ, PostgreSQL, Redis, Next.js 15, HeroUI, HLS.js, and i18next.

## Core Principles
1. **Context is King**: Include ALL necessary documentation, examples, and caveats
2. **Validation Loops**: Provide executable tests/lints the AI can run and fix
3. **Information Dense**: Use keywords and patterns from the codebase
4. **Progressive Success**: Start simple, validate, then enhance
5. **Global rules**: Be sure to follow all rules in CLAUDE.md

---

## Goal
Create a production-grade multi-language video streaming platform with microservices architecture supporting video transcoding, adaptive streaming, multi-audio tracks, subtitles, and full UI localization - delivering Netflix-like user experience with modern technology stack.

## Why
- **Business value**: Multi-billion dollar streaming market with growing demand for localized content
- **Integration**: Demonstrates cutting-edge full-stack development with multiple runtimes and languages
- **Problems this solves**: Global content delivery, multi-language support, scalable video processing pipeline

## What
A complete streaming platform featuring:
- Multi-audio track video streaming with HLS adaptive bitrate
- Real-time subtitle management and synchronization
- Full UI localization with i18next
- Video transcoding pipeline with Go + FFmpeg
- High-performance streaming service in Rust
- Modern frontend with Next.js 15 App Router
- Microservices communication via RabbitMQ
- Multi-language content metadata in PostgreSQL JSONB

### Success Criteria
- [ ] Users can upload videos and they auto-transcode to multiple resolutions (240p-4K)
- [ ] Adaptive streaming works across devices with HLS.js
- [ ] Multiple audio tracks can be switched during playback
- [ ] Subtitles synchronize properly and can be toggled
- [ ] UI supports multiple languages with i18next
- [ ] Content metadata stored with multi-language support
- [ ] Real-time video processing queue with job status updates
- [ ] Authentication and user management system
- [ ] Content discovery and search functionality

## All Needed Context

### Documentation & References
```yaml
# MUST READ - Include these in your context window
- url: https://bun.sh/docs
  why: Bun runtime performance optimizations and API patterns
  
- url: https://elysiajs.com/introduction.html
  why: ElysiaJS API framework patterns and TypeScript integration
  
- url: https://video-dev.github.io/hls.js/stable/docs/
  why: HLS.js implementation for adaptive video streaming
  
- url: https://nextjs.org/docs/app
  why: Next.js 15 App Router patterns for streaming applications
  
- url: https://ffmpeg.org/documentation.html
  why: FFmpeg video transcoding and processing commands
  
- url: https://tokio.rs/tokio/tutorial
  why: Rust async patterns for high-performance streaming
  
- url: https://www.rabbitmq.com/docs/streams
  why: RabbitMQ Streams for video processing job queues
  
- url: https://www.postgresql.org/docs/current/datatype-json.html
  why: PostgreSQL JSONB for multi-language content storage
  
- url: https://react.i18next.com/
  why: i18next React integration for UI localization
  
- url: https://nextui.org/
  why: HeroUI component library for modern streaming UI
  
- url: https://developer.mozilla.org/en-US/docs/Web/API/MediaSource
  why: MediaSource Extensions for custom video player features

- url: https://highscalability.com/designing-netflix/
  why: Netflix architecture patterns and scalability lessons

- url: https://tools.ietf.org/html/rfc8216
  why: HLS protocol specification for adaptive streaming
```

### Current Codebase tree
```bash
.
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md
│   └── EXAMPLE_multi_agent_prp.md
├── use-cases/
│   ├── pydantic-ai/
│   ├── mcp-server/
│   └── agent-factory-with-subagents/
├── CLAUDE.md
├── INITIAL.md
└── README.md
```

### Desired Codebase tree with files to be added and responsibility of file
```bash
multi-language-streaming-platform/
├── backend/
│   ├── api-gateway/                    # Bun + ElysiaJS - Main API server
│   │   ├── src/
│   │   │   ├── index.ts               # Main server entry point
│   │   │   ├── routes/                # API route handlers
│   │   │   │   ├── auth.ts           # Authentication routes
│   │   │   │   ├── content.ts        # Content management
│   │   │   │   ├── user.ts           # User profile management
│   │   │   │   └── streaming.ts      # Streaming endpoints
│   │   │   ├── middleware/            # Request processing
│   │   │   │   ├── auth.ts           # JWT authentication
│   │   │   │   ├── cors.ts           # CORS configuration
│   │   │   │   └── validation.ts     # Request validation
│   │   │   ├── services/              # Business logic
│   │   │   │   ├── authService.ts    # User authentication
│   │   │   │   ├── contentService.ts # Content operations
│   │   │   │   └── streamingService.ts # Stream management
│   │   │   ├── models/                # Data models
│   │   │   │   ├── User.ts           # User entity
│   │   │   │   ├── Content.ts        # Video content entity
│   │   │   │   └── StreamingSession.ts # Streaming session
│   │   │   └── utils/                 # Helper utilities
│   │   │       ├── database.ts       # PostgreSQL connection
│   │   │       ├── redis.ts          # Redis client
│   │   │       └── rabbitmq.ts       # Message queue client
│   │   ├── package.json               # Bun dependencies
│   │   ├── tsconfig.json             # TypeScript config
│   │   └── .env.example              # Environment variables
│   │
│   ├── video-transcoding/             # Go + FFmpeg service
│   │   ├── cmd/
│   │   │   └── main.go               # Service entry point
│   │   ├── internal/
│   │   │   ├── handlers/             # HTTP handlers
│   │   │   │   ├── upload.go        # Video upload handling
│   │   │   │   └── transcode.go     # Transcoding job management
│   │   │   ├── services/             # Business logic
│   │   │   │   ├── transcoder.go    # FFmpeg orchestration
│   │   │   │   ├── storage.go       # File storage management
│   │   │   │   └── queue.go         # RabbitMQ integration
│   │   │   ├── models/               # Data structures
│   │   │   │   ├── job.go           # Transcoding job
│   │   │   │   └── video.go         # Video metadata
│   │   │   └── config/               # Configuration
│   │   │       └── config.go        # Environment configuration
│   │   ├── pkg/
│   │   │   ├── ffmpeg/              # FFmpeg wrapper
│   │   │   │   ├── transcoder.go    # Transcoding logic
│   │   │   │   └── probe.go         # Video analysis
│   │   │   └── storage/             # File storage
│   │   │       └── s3.go            # S3-compatible storage
│   │   ├── go.mod                    # Go dependencies
│   │   ├── go.sum                    # Dependency checksums
│   │   └── Dockerfile               # Container configuration
│   │
│   ├── streaming-service/            # Rust high-performance streaming
│   │   ├── src/
│   │   │   ├── main.rs              # Service entry point
│   │   │   ├── handlers/            # Request handlers
│   │   │   │   ├── stream.rs        # Streaming endpoints
│   │   │   │   └── manifest.rs      # HLS manifest generation
│   │   │   ├── services/            # Core logic
│   │   │   │   ├── stream_manager.rs # Stream session management
│   │   │   │   ├── cdn_manager.rs   # CDN integration
│   │   │   │   └── analytics.rs     # Streaming analytics
│   │   │   ├── models/              # Data structures
│   │   │   │   ├── stream.rs        # Stream metadata
│   │   │   │   └── session.rs       # User session
│   │   │   └── utils/               # Utilities
│   │   │       ├── hls.rs           # HLS utilities
│   │   │       └── cache.rs         # Redis caching
│   │   ├── Cargo.toml               # Rust dependencies
│   │   └── Dockerfile               # Container configuration
│   │
│   └── shared/
│       ├── database/                 # Database schemas
│       │   ├── migrations/          # SQL migration files
│       │   │   ├── 001_users.sql    # User table
│       │   │   ├── 002_content.sql  # Content table
│       │   │   ├── 003_streaming_sessions.sql # Sessions
│       │   │   └── 004_transcoding_jobs.sql # Job queue
│       │   └── init.sql             # Initial database setup
│       └── message-queue/           # RabbitMQ configuration
│           ├── exchanges.json       # Exchange definitions
│           └── queues.json          # Queue configurations
│
├── frontend/                        # Next.js 15 streaming app
│   ├── src/
│   │   ├── app/                     # App Router structure
│   │   │   ├── globals.css          # Global styles
│   │   │   ├── layout.tsx           # Root layout
│   │   │   ├── page.tsx             # Home page
│   │   │   ├── auth/                # Authentication pages
│   │   │   │   ├── login/
│   │   │   │   │   └── page.tsx     # Login page
│   │   │   │   └── signup/
│   │   │   │       └── page.tsx     # Signup page
│   │   │   ├── browse/              # Content browsing
│   │   │   │   ├── page.tsx         # Browse page
│   │   │   │   └── [category]/
│   │   │   │       └── page.tsx     # Category pages
│   │   │   ├── watch/               # Video player
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx     # Video player page
│   │   │   ├── profile/             # User profile
│   │   │   │   └── page.tsx         # Profile management
│   │   │   └── search/              # Search functionality
│   │   │       └── page.tsx         # Search results
│   │   ├── components/              # Reusable components
│   │   │   ├── ui/                  # HeroUI components
│   │   │   │   ├── Button.tsx       # Custom button
│   │   │   │   ├── Modal.tsx        # Modal dialogs
│   │   │   │   └── Card.tsx         # Content cards
│   │   │   ├── video/               # Video-related components
│   │   │   │   ├── VideoPlayer.tsx  # HLS.js video player
│   │   │   │   ├── VideoCard.tsx    # Content preview card
│   │   │   │   ├── AudioTrackSelector.tsx # Audio language selector
│   │   │   │   └── SubtitleSelector.tsx # Subtitle selector
│   │   │   ├── layout/              # Layout components
│   │   │   │   ├── Header.tsx       # Site header
│   │   │   │   ├── Sidebar.tsx      # Navigation sidebar
│   │   │   │   └── Footer.tsx       # Site footer
│   │   │   └── common/              # Common components
│   │   │       ├── LanguageSelector.tsx # UI language switcher
│   │   │       ├── LoadingSpinner.tsx # Loading indicator
│   │   │       └── ErrorBoundary.tsx # Error handling
│   │   ├── hooks/                   # Custom React hooks
│   │   │   ├── useAuth.ts           # Authentication hook
│   │   │   ├── useVideo.ts          # Video playback hook
│   │   │   ├── useLocalization.ts   # i18next hook
│   │   │   └── useApi.ts            # API integration hook
│   │   ├── lib/                     # Utility libraries
│   │   │   ├── api.ts               # API client
│   │   │   ├── auth.ts              # Authentication utilities
│   │   │   ├── i18n.ts              # i18next configuration
│   │   │   └── constants.ts         # Application constants
│   │   ├── store/                   # State management
│   │   │   ├── authStore.ts         # User authentication state
│   │   │   ├── videoStore.ts        # Video playback state
│   │   │   └── localizationStore.ts # Localization state
│   │   └── types/                   # TypeScript definitions
│   │       ├── api.ts               # API response types
│   │       ├── video.ts             # Video-related types
│   │       └── user.ts              # User-related types
│   ├── public/
│   │   ├── locales/                 # i18next translations
│   │   │   ├── en/
│   │   │   │   └── common.json      # English translations
│   │   │   ├── es/
│   │   │   │   └── common.json      # Spanish translations
│   │   │   ├── fr/
│   │   │   │   └── common.json      # French translations
│   │   │   └── de/
│   │   │       └── common.json      # German translations
│   │   └── assets/                  # Static assets
│   │       ├── icons/               # UI icons
│   │       └── images/              # Images
│   ├── package.json                 # Dependencies
│   ├── next.config.js               # Next.js configuration
│   ├── tailwind.config.js           # TailwindCSS config
│   └── tsconfig.json               # TypeScript config
│
├── infrastructure/                  # Infrastructure as code
│   ├── docker/
│   │   ├── docker-compose.yml       # Development environment
│   │   └── Dockerfile.*             # Service containers
│   ├── terraform/                   # Cloud infrastructure
│   │   ├── main.tf                  # Main configuration
│   │   ├── variables.tf             # Variable definitions
│   │   └── outputs.tf               # Output values
│   └── k8s/                        # Kubernetes manifests
│       ├── namespace.yaml           # Namespace definition
│       ├── api-gateway.yaml         # API gateway deployment
│       ├── transcoding-service.yaml # Transcoding service
│       └── streaming-service.yaml   # Streaming service
│
├── tests/                          # Testing suites
│   ├── api-gateway/                # API gateway tests
│   │   ├── unit/                   # Unit tests
│   │   ├── integration/            # Integration tests
│   │   └── e2e/                    # End-to-end tests
│   ├── transcoding/                # Transcoding service tests
│   ├── streaming/                  # Streaming service tests
│   └── frontend/                   # Frontend tests
│       ├── components/             # Component tests
│       ├── pages/                  # Page tests
│       └── e2e/                    # E2E tests
│
├── scripts/                        # Development scripts
│   ├── setup.sh                    # Environment setup
│   ├── build.sh                    # Build all services
│   ├── test.sh                     # Run all tests
│   └── deploy.sh                   # Deployment script
│
├── docs/                           # Documentation
│   ├── api/                        # API documentation
│   ├── architecture/               # System architecture
│   ├── deployment/                 # Deployment guides
│   └── development/                # Development guides
│
├── .env.example                    # Environment variables template
├── .gitignore                      # Git ignore rules
├── README.md                       # Project documentation
└── package.json                    # Root project configuration
```

### Known Gotchas of our codebase & Library Quirks
```javascript
// CRITICAL: Bun has higher memory usage than Node.js but 2.5x performance improvement
// CRITICAL: ElysiaJS requires TypeScript strict mode for type safety
// CRITICAL: FFmpeg in Go requires proper goroutine management for concurrent transcoding
// CRITICAL: Rust async with Tokio requires careful lifetime management in streaming contexts
// CRITICAL: RabbitMQ Streams require different patterns than traditional queues
// CRITICAL: PostgreSQL JSONB requires GIN indexes for optimal query performance
// CRITICAL: HLS.js requires CORS headers for cross-origin video streaming
// CRITICAL: i18next namespace loading can cause hydration mismatches in SSR
// CRITICAL: Next.js 15 App Router has breaking changes from Pages Router
// CRITICAL: Video transcoding is CPU/GPU intensive - requires resource limiting
```

## Implementation Blueprint

### Data models and structure

Create the core data models to ensure type safety and consistency across services.

```typescript
// Shared TypeScript models
interface User {
  id: string;
  email: string;
  username: string;
  profile: {
    displayName: string;
    avatar?: string;
    preferredLanguage: string;
    preferredAudioLanguage: string;
    preferredSubtitleLanguage: string;
  };
  subscription: {
    tier: 'free' | 'premium' | 'family';
    expiresAt: Date;
  };
  createdAt: Date;
  updatedAt: Date;
}

interface VideoContent {
  id: string;
  title: Record<string, string>; // Multi-language titles
  description: Record<string, string>; // Multi-language descriptions
  metadata: {
    duration: number;
    releaseDate: Date;
    genre: string[];
    rating: string;
    languages: {
      audio: string[];
      subtitles: string[];
    };
  };
  media: {
    originalFile: string;
    transcodedVersions: TranscodedVersion[];
    thumbnails: string[];
    manifest: string; // HLS manifest URL
  };
  status: 'uploaded' | 'processing' | 'ready' | 'failed';
  createdAt: Date;
  updatedAt: Date;
}

interface TranscodedVersion {
  resolution: '240p' | '480p' | '720p' | '1080p' | '4k';
  bitrate: number;
  codec: 'h264' | 'h265' | 'av1';
  fileUrl: string;
  audioTracks: AudioTrack[];
}

interface AudioTrack {
  language: string;
  codec: 'aac' | 'mp3' | 'opus';
  bitrate: number;
  fileUrl: string;
}

// PostgreSQL JSONB schema
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  username VARCHAR(100) UNIQUE NOT NULL,
  profile JSONB NOT NULL,
  subscription JSONB NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE content (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  title JSONB NOT NULL, -- Multi-language support
  description JSONB NOT NULL,
  metadata JSONB NOT NULL,
  media JSONB NOT NULL,
  status VARCHAR(50) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- GIN indexes for JSONB queries
CREATE INDEX idx_content_metadata ON content USING GIN (metadata);
CREATE INDEX idx_content_title ON content USING GIN (title);
CREATE INDEX idx_user_profile ON users USING GIN (profile);
```

### List of tasks to be completed to fulfill the PRP in the order they should be completed

```yaml
Task 1: Infrastructure Setup
CREATE infrastructure/docker/docker-compose.yml:
  - PATTERN: Multi-container development environment
  - PostgreSQL with JSONB support
  - Redis for caching
  - RabbitMQ with management UI
  - S3-compatible storage (MinIO)

CREATE backend/shared/database/migrations/:
  - PATTERN: Sequential migration files
  - User authentication and profiles
  - Multi-language content metadata
  - Transcoding job queue tables

Task 2: API Gateway with Bun + ElysiaJS
CREATE backend/api-gateway/src/index.ts:
  - PATTERN: ElysiaJS server with JWT middleware
  - CORS configuration for video streaming
  - Rate limiting and request validation
  - Health check endpoints

CREATE backend/api-gateway/src/routes/:
  - PATTERN: RESTful API design
  - Authentication (login, register, refresh)
  - Content CRUD operations
  - Streaming session management
  - File upload handling

Task 3: Video Transcoding Service (Go + FFmpeg)
CREATE backend/video-transcoding/cmd/main.go:
  - PATTERN: Go HTTP server with goroutine pools
  - RabbitMQ consumer for transcoding jobs
  - FFmpeg wrapper with concurrent processing
  - Progress tracking and status updates

CREATE backend/video-transcoding/pkg/ffmpeg/:
  - PATTERN: Quality ladder generation (240p-4K)
  - Multi-audio track extraction
  - Subtitle processing and synchronization
  - HLS manifest generation

Task 4: High-Performance Streaming Service (Rust)
CREATE backend/streaming-service/src/main.rs:
  - PATTERN: Tokio async HTTP server
  - HLS manifest serving with caching
  - Stream analytics and monitoring
  - CDN integration for global delivery

CREATE backend/streaming-service/src/services/:
  - PATTERN: Stream session management
  - Redis-backed caching layer
  - Real-time streaming metrics
  - Adaptive bitrate logic

Task 5: Frontend Application (Next.js 15)
CREATE frontend/src/app/layout.tsx:
  - PATTERN: App Router with i18next SSR
  - HeroUI theme provider setup
  - Authentication context provider
  - Global state management

CREATE frontend/src/components/video/VideoPlayer.tsx:
  - PATTERN: HLS.js integration with React
  - Multi-audio track switching
  - Subtitle management and display
  - Adaptive streaming controls

Task 6: Internationalization Implementation
CREATE frontend/public/locales/:
  - PATTERN: Namespace-based translations
  - Video player controls in multiple languages
  - Content metadata translations
  - UI element localizations

CREATE frontend/src/lib/i18n.ts:
  - PATTERN: i18next configuration with SSR
  - Dynamic namespace loading
  - Language detection and persistence
  - Fallback language handling

Task 7: Message Queue Integration
CREATE backend/shared/message-queue/:
  - PATTERN: RabbitMQ stream configuration
  - Job processing workflows
  - Error handling and retry logic
  - Dead letter queue setup

Task 8: Testing and Validation
CREATE tests/ directories:
  - PATTERN: Comprehensive test coverage
  - API integration tests
  - Video transcoding validation
  - Frontend component testing
  - E2E streaming workflow tests
```

### Per task pseudocode as needed

```typescript
// Task 2: API Gateway Implementation
// backend/api-gateway/src/index.ts
import { Elysia } from 'elysia';
import { cors } from '@elysiajs/cors';
import { jwt } from '@elysiajs/jwt';

const app = new Elysia()
  .use(cors({
    origin: process.env.FRONTEND_URL,
    credentials: true,
    // CRITICAL: Required for video streaming
    exposedHeaders: ['content-range', 'accept-ranges']
  }))
  .use(jwt({
    name: 'jwt',
    secret: process.env.JWT_SECRET
  }))
  // PATTERN: Middleware pipeline
  .derive(({ jwt, headers }) => ({
    // Authentication middleware
    user: verifyAuthToken(headers.authorization, jwt)
  }))
  .post('/api/auth/login', async ({ body, jwt, set }) => {
    // PATTERN: JWT authentication
    const user = await authenticateUser(body.email, body.password);
    const token = await jwt.sign({ userId: user.id });
    
    set.headers['set-cookie'] = `token=${token}; HttpOnly; Secure; SameSite=strict`;
    return { user, token };
  })
  .post('/api/content/upload', async ({ body, user }) => {
    // PATTERN: File upload with validation
    const uploadResult = await uploadVideoFile(body.file, user.id);
    
    // CRITICAL: Queue transcoding job immediately
    await rabbitMQClient.publish('video.transcode', {
      contentId: uploadResult.id,
      originalFile: uploadResult.filePath,
      userId: user.id
    });
    
    return uploadResult;
  })
  .listen(3000);

// Task 3: Video Transcoding Service
// backend/video-transcoding/internal/services/transcoder.go
package services

import (
    "context"
    "os/exec"
    "sync"
)

type TranscodingService struct {
    // PATTERN: Semaphore for concurrent job control
    semaphore chan struct{}
    maxConcurrent int
}

func (s *TranscodingService) ProcessVideo(ctx context.Context, job TranscodingJob) error {
    // CRITICAL: Acquire semaphore for concurrency control
    s.semaphore <- struct{}{}
    defer func() { <-s.semaphore }()
    
    // PATTERN: Quality ladder generation
    resolutions := []string{"240p", "480p", "720p", "1080p", "4k"}
    var wg sync.WaitGroup
    
    for _, resolution := range resolutions {
        wg.Add(1)
        go func(res string) {
            defer wg.Done()
            
            // CRITICAL: FFmpeg command with hardware acceleration
            cmd := exec.CommandContext(ctx, "ffmpeg",
                "-i", job.InputFile,
                "-c:v", "libx264",
                "-preset", "fast",
                "-crf", "23",
                "-s", getResolutionSize(res),
                "-c:a", "aac",
                "-b:a", "128k",
                "-f", "hls",
                "-hls_time", "4",
                "-hls_playlist_type", "vod",
                getOutputPath(job.ContentID, res))
            
            if err := cmd.Run(); err != nil {
                s.notifyTranscodingError(job.ContentID, res, err)
                return
            }
            
            s.notifyTranscodingComplete(job.ContentID, res)
        }(resolution)
    }
    
    wg.Wait()
    return nil
}

// Task 5: Video Player Component
// frontend/src/components/video/VideoPlayer.tsx
import { useRef, useEffect, useState } from 'react';
import Hls from 'hls.js';
import { useTranslation } from 'react-i18next';

interface VideoPlayerProps {
  src: string;
  audioTracks: AudioTrack[];
  subtitles: SubtitleTrack[];
}

export function VideoPlayer({ src, audioTracks, subtitles }: VideoPlayerProps) {
  const videoRef = useRef<HTMLVideoElement>(null);
  const hlsRef = useRef<Hls | null>(null);
  const { t } = useTranslation('video');
  const [currentAudioTrack, setCurrentAudioTrack] = useState(0);
  const [currentSubtitle, setCurrentSubtitle] = useState(-1);

  useEffect(() => {
    if (videoRef.current && Hls.isSupported()) {
      // PATTERN: HLS.js initialization with error handling
      const hls = new Hls({
        enableWorker: true,
        lowLatencyMode: false,
        backBufferLength: 90
      });
      
      hls.loadSource(src);
      hls.attachMedia(videoRef.current);
      
      // CRITICAL: Audio track switching support
      hls.on(Hls.Events.MANIFEST_PARSED, () => {
        // Enable audio track selection
        const audioTracksList = hls.audioTracks;
        setAvailableAudioTracks(audioTracksList);
      });
      
      // GOTCHA: Handle HLS errors gracefully
      hls.on(Hls.Events.ERROR, (event, data) => {
        if (data.fatal) {
          switch (data.type) {
            case Hls.ErrorTypes.NETWORK_ERROR:
              hls.startLoad();
              break;
            case Hls.ErrorTypes.MEDIA_ERROR:
              hls.recoverMediaError();
              break;
            default:
              hls.destroy();
              break;
          }
        }
      });
      
      hlsRef.current = hls;
    }
    
    return () => {
      if (hlsRef.current) {
        hlsRef.current.destroy();
      }
    };
  }, [src]);

  const switchAudioTrack = (trackIndex: number) => {
    if (hlsRef.current) {
      hlsRef.current.audioTrack = trackIndex;
      setCurrentAudioTrack(trackIndex);
    }
  };

  const toggleSubtitles = (subtitleIndex: number) => {
    if (hlsRef.current) {
      hlsRef.current.subtitleTrack = subtitleIndex;
      setCurrentSubtitle(subtitleIndex);
    }
  };

  return (
    <div className="relative">
      <video
        ref={videoRef}
        controls
        className="w-full h-auto"
        crossOrigin="anonymous" // CRITICAL for subtitle loading
      />
      
      {/* Audio Track Selector */}
      <div className="absolute top-4 right-4">
        <select 
          value={currentAudioTrack}
          onChange={(e) => switchAudioTrack(parseInt(e.target.value))}
          className="bg-black bg-opacity-50 text-white"
        >
          {audioTracks.map((track, index) => (
            <option key={index} value={index}>
              {t('audio.language', { language: track.language })}
            </option>
          ))}
        </select>
      </div>
      
      {/* Subtitle Selector */}
      <div className="absolute top-12 right-4">
        <select 
          value={currentSubtitle}
          onChange={(e) => toggleSubtitles(parseInt(e.target.value))}
          className="bg-black bg-opacity-50 text-white"
        >
          <option value={-1}>{t('subtitles.none')}</option>
          {subtitles.map((subtitle, index) => (
            <option key={index} value={index}>
              {t('subtitles.language', { language: subtitle.language })}
            </option>
          ))}
        </select>
      </div>
    </div>
  );
}
```

### Integration Points
```yaml
ENVIRONMENT VARIABLES:
  - Backend services: Database URL, Redis URL, RabbitMQ URL, JWT secrets
  - Frontend: API base URL, supported languages, analytics keys
  - Transcoding: FFmpeg path, storage credentials, quality presets
  - Streaming: CDN endpoints, cache TTL, analytics endpoints

MESSAGE QUEUES:
  - Exchange: "video.exchange" (topic type)
  - Queues: "video.transcode", "video.complete", "video.failed"
  - Routing: Content type and priority-based routing
  - DLQ: Dead letter queue for failed processing

STORAGE:
  - Original videos: S3-compatible storage with versioning
  - Transcoded content: CDN with global distribution
  - Thumbnails: Optimized image storage with multiple sizes
  - Metadata: PostgreSQL with JSONB indexing

CDN CONFIGURATION:
  - Origin servers: Multiple regions for redundancy
  - Edge caching: 24-hour TTL for video segments
  - Geo-blocking: Content licensing compliance
  - Analytics: Real-time streaming metrics
```

## Validation Loop

### Level 1: Service Health & Syntax
```bash
# Backend services syntax checking
cd backend/api-gateway && bun run type-check
cd backend/video-transcoding && go build ./...
cd backend/streaming-service && cargo check

# Frontend syntax and type checking
cd frontend && npm run type-check && npm run lint

# Infrastructure validation
cd infrastructure && terraform validate
cd infrastructure/docker && docker-compose config

# Expected: No errors. If errors, READ and fix before proceeding.
```

### Level 2: Unit Tests
```bash
# API Gateway tests
cd backend/api-gateway && bun test

# Video transcoding tests
cd backend/video-transcoding && go test ./...

# Streaming service tests
cd backend/streaming-service && cargo test

# Frontend component tests
cd frontend && npm run test

# Expected: All tests pass. If failing, debug and fix issues.
```

### Level 3: Integration Tests
```bash
# Start all services with Docker Compose
docker-compose up -d

# Wait for services to be ready
./scripts/wait-for-services.sh

# Test video upload and transcoding pipeline
curl -X POST http://localhost:3000/api/content/upload \
  -H "Authorization: Bearer $TEST_TOKEN" \
  -F "file=@test-video.mp4"

# Verify transcoding job processing
curl http://localhost:3000/api/content/{contentId}/status

# Test streaming endpoint
curl -I http://localhost:8080/stream/{contentId}/playlist.m3u8

# Expected: 
# - Video uploads successfully
# - Transcoding jobs complete within 5 minutes
# - HLS playlists are accessible
# - Multiple quality levels available
```

### Level 4: End-to-End Tests
```bash
# Frontend E2E tests with Playwright
cd frontend && npm run test:e2e

# Full user workflow test:
# 1. User registration and login
# 2. Video content browsing
# 3. Video playback with quality switching
# 4. Audio track switching during playback
# 5. Subtitle toggling
# 6. UI language switching
# 7. Search functionality

# Performance benchmarks:
# - Video startup time < 2 seconds
# - Quality switching < 1 second
# - Audio track switching < 0.5 seconds
# - UI language switching < 0.3 seconds
```

## Final Validation Checklist
- [ ] All services start successfully: `docker-compose up -d`
- [ ] No syntax errors: All type checks pass
- [ ] No unit test failures: `./scripts/test-all.sh`
- [ ] Video upload works: API accepts video files
- [ ] Transcoding completes: Multiple resolutions generated
- [ ] HLS streaming works: Video playback in browser
- [ ] Audio tracks switch: Multiple language support
- [ ] Subtitles display: Synchronization with video
- [ ] UI localization works: i18next translations load
- [ ] Search functionality: Content discovery works
- [ ] User authentication: JWT-based auth flow
- [ ] Database operations: JSONB queries perform well
- [ ] Message queue processing: Jobs complete successfully
- [ ] CDN integration: Global content delivery
- [ ] Mobile responsiveness: Cross-device compatibility
- [ ] Performance benchmarks: Sub-2s video startup

---

## Anti-Patterns to Avoid
- ❌ Don't skip video transcoding validation - broken video files will crash FFmpeg
- ❌ Don't ignore HLS CORS configuration - video streaming will fail
- ❌ Don't hardcode video resolutions - make them configurable for different content types
- ❌ Don't skip concurrency limits - transcoding can overwhelm servers
- ❌ Don't ignore subtitle synchronization - timing issues break user experience
- ❌ Don't skip database indexing - JSONB queries will be slow without GIN indexes
- ❌ Don't ignore streaming analytics - essential for performance monitoring
- ❌ Don't skip authentication on streaming endpoints - content piracy risk
- ❌ Don't ignore CDN cache invalidation - stale content will be served
- ❌ Don't skip error boundaries in React - video player errors will crash the app

## Confidence Score: 8/10

High confidence due to:
- Comprehensive research of Netflix-like streaming architecture
- Well-documented technology stack with proven performance
- Clear microservices separation of concerns
- Established patterns for video transcoding and streaming
- Strong frontend framework with modern React patterns
- Comprehensive validation gates at multiple levels

Minor uncertainty on:
- FFmpeg transcoding performance optimization in containerized environments
- RabbitMQ Streams configuration for high-throughput video processing
- CDN integration complexity and global content delivery optimization

The architecture follows proven Netflix patterns with modern technology stack providing excellent foundation for implementation success.