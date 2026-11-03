# Development Plan: Markdown Editor

## Overview
Create a single-file markdown editor with live preview, file load/save capabilities, and light/dark mode support that runs in a modern web browser.

## Core Requirements

### 1. User Interface
- Split-pane layout with editor on left and preview on right
- Responsive design that stacks vertically on mobile (<768px)
- Editor pane with textarea for markdown input
- Preview pane with rendered markdown output
- Pane headers with labels and action buttons
- Status bar at bottom showing file info and character count
- Theme toggle button (light/dark mode)

### 2. Markdown Functionality
- Integrated marked.js library for markdown parsing
- Real-time preview updates as user types
- Support for standard markdown elements:
  - Headers (H1-H6)
  - Paragraphs and line breaks
  - Bold, italic, and strikethrough text
  - Code blocks and inline code
  - Blockquotes
  - Ordered and unordered lists
  - Tables
  - Horizontal rules
  - Links and images
- Tab key handling for indentation in editor

### 3. File Operations
- Load local markdown/text files via file picker
- Save current content as markdown file
- Display loaded filename in status bar
- Default to "untitled.md" when saving new content
- Maintain reference to currently loaded file

### 4. Theme System
- Light and dark color schemes using CSS variables
- System preference detection on first load
- User theme preference persistence via localStorage
- Smooth transition between themes (0.3s)
- Visual indication of current theme (🌙/☀️ icon)
- All UI elements adapt to theme (backgrounds, text, borders, inputs)

### 5. Technical Implementation
- Single HTML file with embedded CSS and JavaScript
- No external dependencies beyond marked.js CDN
- Vanilla JavaScript (no frameworks)
- Event-driven architecture for UI updates
- Proper cleanup of object URLs to prevent memory leaks
- Accessible ARIA labels for interactive elements

## Implementation Steps

### Phase 1: Basic Structure
1. Create HTML structure with editor and preview panes
2. Add basic styling for layout and typography
3. Implement textarea and preview div
4. Add pane headers with labels

### Phase 2: Markdown Rendering
1. Include marked.js library via CDN
2. Implement updatePreview() function
3. Add real-time event listeners (input, keyup, change)
4. Set up initial preview rendering

### Phase 3: File Operations
1. Implement load file functionality with FileReader API
2. Implement save file functionality with Blob and URL.createObjectURL
3. Add file info display in status bar
4. Add character count display and updates

### Phase 4: UI Enhancements
1. Add responsive design with media queries
2. Implement tab key handling for indentation
3. Add focus states for textarea and preview
4. Improve visual feedback for interactive elements

### Phase 5: Theme System
1. Define CSS variables for light theme
2. Define CSS variables for dark theme using [data-theme="dark"]
3. Implement theme toggle button
4. Add theme persistence with localStorage
5. Implement system preference detection
6. Add smooth transitions for theme changes
7. Update theme icon based on current state

### Phase 6: Polish and Testing
1. Test across different screen sizes
2. Verify file operations work correctly
3. Test theme persistence and switching
4. Validate markdown rendering accuracy
5. Check accessibility and ARIA labels
6. Optimize performance for large documents
7. Test in multiple modern browsers (Chrome, Firefox, Safari, Edge)

## Non-Functional Requirements

### Performance
- Preview updates should be responsive (<100ms delay)
- Efficient DOM updates to prevent layout thrashing
- Memory leak prevention (revoke object URLs)
- Reasonable initial load time

### Usability
- Intuitive interface with clear visual hierarchy
- Consistent spacing and typography
- Appropriate placeholder text and hints
- Keyboard accessibility for all functions
- Clear visual feedback for interactions

### Compatibility
- Works in modern browsers (Chrome, Firefox, Safari, Edge)
- Responsive on mobile and tablet devices
- Graceful degradation if JavaScript fails (basic textarea still usable)
- Follows web accessibility guidelines (WCAG 2.1 AA)

## Future Enhancements (Not in Scope for v1)
- Syntax highlighting in editor
- Customizable themes
- Export to PDF/HTML
- Image upload/paste support
- Spell checking
- Find and replace functionality
- Document outline/navigation
- Version history/undo-redo
- Collaborative editing
- Plugin/extension system

## Dependencies
- marked.js (via CDN): https://cdn.jsdelivr.net/npm/marked/marked.min.js
- No other external dependencies required

## Success Criteria
- User can write markdown in editor pane
- Preview updates in real-time with accurate rendering
- Files can be loaded and saved successfully
- Light/dark mode toggles work and persist
- Interface is usable on both desktop and mobile
- All markdown elements render correctly
- No JavaScript errors in console
- File operations handle edge cases (empty files, large files, etc.)