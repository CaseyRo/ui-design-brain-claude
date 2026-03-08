---
name: ui-design-brain
description: Generate production-grade UI using real component patterns and best practices from 60+ documented interface components. Use when the user asks to build web interfaces, pages, dashboards, forms, navigation, or any UI — ensures modern, minimal, SaaS-quality output grounded in design system conventions rather than generic AI patterns.
user-invocable: false
---

# UI Design Brain — Component Reference Skill

This skill provides a curated knowledge base of 60+ UI component patterns sourced from [component.gallery](https://component.gallery) and enriched with best practices, layout guidance, and usage rules.

**Before writing any UI code**, consult [components.md](components.md) for the full component reference with best practices, aliases, and layout examples.

## Component Quick Reference

| Component | When to use | Key rule |
|-----------|------------|----------|
| **Button** | Trigger actions | Verb-first labels; one primary per section |
| **Card** | Represent an entity | Media → title → meta → action; shadow OR border, not both |
| **Modal** | Focused attention | Trap focus; X + Cancel + Escape to close |
| **Navigation** | Page/section links | 5–7 items max; clear active state |
| **Table** | Structured data | Sticky header; right-align numbers; sortable columns |
| **Tabs** | Switch panels | 2–7 tabs; active indicator; accordion on mobile |
| **Form** | Collect input | Single column; labels above; inline validation on blur |
| **Toast** | Brief confirmation | Auto-dismiss 4–6s; undo action for destructive ops |
| **Alert** | Important status | Semantic colors + icon; max 2 sentences |
| **Drawer** | Secondary panel | Right for detail, left for nav; 320–480px desktop |
| **Search input** | Find content | Cmd/Ctrl+K shortcut; debounce 200–300ms |
| **Empty state** | No data | Illustration + headline + CTA; positive framing |
| **Skeleton** | Loading placeholder | Match actual layout shape; shimmer animation |
| **Badge** | Status/metadata label | 1–2 words; pill shape for status; limited color palette |
| **Dropdown menu** | Action/nav options | 7±2 items; destructive actions last in red |

## Common Component Mappings

- "navigation" → Header, Navigation, Breadcrumbs, Tabs
- "form" → Form, Text input, Select, Checkbox, Radio button, Button
- "data display" → Table, Card, List, Badge, Avatar
- "feedback" → Alert, Toast, Modal, Spinner, Progress bar, Empty state
- "input" → Text input, Textarea, Select, Combobox, Datepicker, File upload, Slider
- "overlay" → Modal, Drawer, Popover, Tooltip, Dropdown menu
