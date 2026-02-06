# Minecraft Console Launcher - Design Guidelines

## Design Approach

**Reference-Based Gaming Interface**: Drawing inspiration from modern gaming launchers (Epic Games Launcher, Discord, Steam) with a technical console aesthetic. This combines gaming visual appeal with utility-focused information density.

**Core Principle**: Gaming-grade polish with technical precision - every element should feel responsive, premium, and purposeful.

---

## Typography System

**Primary Font**: "Inter" or "Roboto" (Google Fonts) - clean, modern sans-serif for UI elements
**Console/Code Font**: "JetBrains Mono" or "Fira Code" (Google Fonts) - for chat viewer, commands, technical data

**Hierarchy**:
- Headers: 2xl-3xl, font-bold (launcher title, section headers)
- Subheaders: xl, font-semibold (account names, server info)
- Body: base-lg, font-medium (buttons, labels, status)
- Console/Chat: sm-base, font-mono (chat messages, logs, commands)
- Caption: xs-sm, font-normal (timestamps, helper text)

---

## Layout System

**Spacing Primitives**: Tailwind units of 2, 4, 6, 8, 12, 16
- Component padding: p-4 to p-6
- Section gaps: gap-6 to gap-8
- Card spacing: space-y-4
- Button padding: px-6 py-3

**Grid Structure**: 
- Main layout: Sidebar (280px fixed) + Main content area (flex-1)
- Multi-account cards: grid-cols-1 md:grid-cols-2 gap-4
- Configuration sections: 2-column layout for settings (label + input)

---

## Component Library

### Core Layout

**Sidebar Navigation** (Left, 280px):
- Logo/branding at top with glowing accent
- Navigation items: Dashboard, Accounts, Chat Viewer, Settings, Configs
- Active state: Subtle background with left border accent
- Connection status indicator at bottom with pulsing animation
- Icons from Heroicons (outline style)

**Main Content Area**:
- Full height, scrollable
- Max-width container for readability
- Padding: p-8

### Account Management

**Account Cards** (Grid layout):
- Rounded corners (rounded-xl)
- Elevated appearance with subtle shadow
- Header: Account name + type badge (Online/Offline)
- Body: Username, selected version, proxy status
- Actions: Launch button (prominent), Edit (icon), Delete (icon)
- Status indicator dot (active/inactive)

**Add Account Button**:
- Dashed border card (border-2 border-dashed)
- Centered plus icon (Heroicons)
- Hover state: Solid appearance transform

### Chat Viewer Console

**Terminal-Style Interface**:
- Full-width, fixed height panel (h-96 to h-screen/2)
- Monospace font throughout
- Auto-scroll to bottom
- Message format: `[HH:MM:SS] <Username> Message`
- Scrollbar styled to match theme
- Background: Slightly recessed appearance

**Chat Controls Bar** (Above console):
- Filter options (All/System/Players)
- Clear button
- Auto-scroll toggle
- Export logs button

### Configuration Panel

**Optional Config Menu** (Collapsible):
- Accordion-style sections
- Sections: Auto-Reconnect, Commands, Proxy, AFK Settings
- Each setting: Label (left) + Control (right) in 2-column grid

**Input Fields**:
- Rounded borders (rounded-lg)
- Focused state: Border accent glow effect
- Placeholder text with reduced opacity
- Prefix icons where relevant (lock for password, globe for proxy)

**Toggle Switches**:
- Modern slider design with smooth transition
- Labels adjacent to switch
- Active state clearly differentiated

### Version Selector

**Dropdown Component**:
- Full version list from legacy to latest
- Search/filter capability at top
- Grouped by version type (Release, Snapshot, Beta)
- Selected version displayed prominently
- Icons: Heroicons chevron-down

### Buttons

**Primary Action** (Launch):
- Large, prominent (px-8 py-4)
- Rounded (rounded-lg)
- Icon + Text combination
- Hover: Subtle lift effect (transform translateY)
- Loading state: Spinner icon + "Launching..." text

**Secondary Actions**:
- Medium size (px-4 py-2)
- Rounded (rounded-md)
- Ghost/outline variants for less emphasis

**Icon Buttons** (Edit, Delete):
- Square (w-10 h-10)
- Rounded (rounded-lg)
- Icon only, tooltip on hover

### Status Indicators

**Connection Status Badge**:
- Dot indicator + Text
- States: Connected (pulsing glow), Connecting (animated), Disconnected, Reconnecting
- Position: Fixed in sidebar footer or floating top-right

**Proxy Status**:
- Small badge on account cards
- Icon + "Proxy Active" text
- Tooltip shows proxy address on hover

### Modal Overlays

**Configuration Modals**:
- Centered, max-width (max-w-2xl)
- Semi-transparent backdrop
- Smooth fade-in animation
- Header with title + close button
- Body with form fields
- Footer with Cancel + Save buttons

---

## Animations (Minimal, High-Impact)

**Strategic Use Only**:
- Connection status pulse (subtle, continuous)
- Sidebar item hover: Background fade-in (150ms)
- Button hover: Slight scale (scale-105) and shadow increase
- Modal entry: Fade + scale from 95% to 100%
- Chat messages: Fade-in on arrival
- **NO** random movements, excessive transitions, or distracting effects

---

## Icons

**Library**: Heroicons (via CDN)
- Outline style for navigation and secondary actions
- Solid style for status indicators and active states
- Size consistency: w-5 h-5 for UI elements, w-6 h-6 for prominent actions

---

## Images

**No hero images required** - This is a utility application, not a marketing site.

**Logo/Branding**: 
- Minecraft-inspired logo/icon in sidebar header
- Accent treatment (glow effect)

**Account Avatars** (Optional):
- If implemented: 48x48px rounded avatar images
- Placeholder: User initials in circle with accent background

---

## Accessibility

- Keyboard navigation throughout (tab indices logical)
- Focus indicators visible on all interactive elements
- ARIA labels for icon-only buttons
- Status changes announced for screen readers
- Sufficient contrast ratios maintained (verified)
- Form inputs with associated labels

---

## Responsive Considerations

**Desktop-First** (This is primarily a desktop app):
- Minimum viewport: 1280px recommended
- Sidebar collapses to icons-only on smaller screens (<1024px)
- Account grid: 2 columns desktop, 1 column tablet
- Chat viewer maintains readability at all sizes