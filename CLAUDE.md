# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Team Content Management System (CMS) project designed as a multi-repository architecture with clear separation between backend and frontend services. The project enables teams to create, organize, share, and collaborate on content in a unified knowledge hub.

## Repository Structure

This is a parent project containing two independent sub-projects:

- `cms-backend-service/` - Node.js/Express API service with Redis/Keyv data storage
- `cms-ui-frontend/` - Static HTML/JS frontend with Vue 3 (planned), currently prototype HTML files

## Architecture

**Multi-Repository Design**: Backend and frontend are developed, tested, and deployed independently to enable:
- Technology flexibility (can swap out either component independently)
- Team autonomy and parallel development
- Independent deployment and scaling
- Clear API contracts between services

**Current Technology Stack**:
- **Backend**: Node.js, Express.js, Keyv (Redis abstraction), TypeScript, Jest
- **Frontend**: Vue 3 (planned), Tailwind CSS, Vite (planned)
- **Database**: Redis (Valkey)
- **File Storage**: AWS S3
- **Authentication**: OAuth 2.0
- **Hosting**: DigitalOcean

## Development Commands

**Note**: This repository currently contains planning documents and prototype HTML files. Each sub-project will have its own package.json with specific build/test commands once implemented.

For the planned backend service (`cms-backend-service/`):
```bash
npm install          # Install dependencies
npm run dev          # Start development server
npm test             # Run Jest unit tests
npm run build        # Build TypeScript to JavaScript
npm start            # Start production server
```

For the planned frontend (`cms-ui-frontend/`):
```bash
npm install          # Install dependencies
npm run dev          # Start Vite development server
npm run build        # Build for production
npm run preview      # Preview production build
npm test             # Run frontend tests
```

## Key Features (Planned)

1. **User Management**: OAuth 2.0 authentication, role-based access control, team management
2. **Content Creation**: Rich text editor, media management, version control, collaborative editing
3. **Content Discovery**: Full-text search, categorization, tagging, bookmarking
4. **Collaboration**: Real-time commenting, notifications, content sharing
5. **Administration**: Dashboard, audit logs, backup/restore, system configuration
6. **Privacy & Compliance**: GDPR compliance, PII handling, data retention policies

## Data Models (Backend)

All entities extend a `BaseModel` interface with:
- `key`: Unique identifier (string)
- `version`: Version number for optimistic locking
- `createdAt`/`updatedAt`: Timestamps
- `status`: Entity status (active, inactive, archived, etc.)

Key entities:
- `Content`: Documents with title, body, author, category, tags, permissions
- `User`: Profile with name, email, roles, team memberships
- `Team`: Groups with members and permissions

## API Design Patterns

- RESTful endpoints using Express Router
- Consistent error handling middleware
- Input validation using Joi schemas
- Key-based entity identification (not sequential IDs)
- JSON responses with proper HTTP status codes

## Development Phases

1. **Phase 1 (MVP)**: Basic auth, content CRUD, file uploads, simple search
2. **Phase 2**: Teams, RBAC, tagging, version control, commenting
3. **Phase 3**: Real-time collaboration, notifications, admin dashboard
4. **Phase 4**: Performance optimization, security audits, production deployment

## Current Status

The project is in the planning/design phase with:
- Comprehensive project documentation in `docs/`
- Prototype landing page and interactive plan in `cms-ui-frontend/`
- Detailed technical specifications for both services
- Architecture decisions documented

## Important Notes

- Maintain the independent repository structure for backend/frontend
- Follow the established data models and API patterns
- Prioritize security and privacy by design
- Use TypeScript for type safety in both backend and frontend
- Implement comprehensive testing (Jest for backend, frontend testing TBD)
- Follow the phased development approach to maintain deliverable milestones