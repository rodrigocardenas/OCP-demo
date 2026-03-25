# 📋 PLAN DE MEJORA - DESAFÍOS DEL PUEBLO MODULE
**Fecha:** 25 de Marzo, 2026  
**Estado:** En Planificación  
**Objetivo:** Modernizar diseño de "Desafíos del Pueblo" a Dark Theme + Sobrio Professional

---

## 🎯 OBJETIVOS GENERALES

### Current State (Light Theme - Orange/Yellow)
- Header: Gradiente naranja (#ff6b35 → #f7931e)
- Background: Light gradient (#fff3e0 → #f3e5f5)
- Cards: Blanco con sombras suaves
- Stats bar: Blanco con números naranjas
- Featured card: Amarillo claro con borde naranja
- Accents: Naranja, amarillo, azules claros
- **Problema:** Diseño casual y cálido, inconsistente con dashboard modernizado

### Target State (Dark Theme + Professional)
- Header: Gris oscuro profesional con accent color
- Background: Dark gradient sofisticado con fade (similar a dashboard)
- Cards: Dark backgrounds (#1E2639) con bordes sutiles
- Stats bar: Dark background con colores primarios
- Featured card: Dark card con gradient overlay sutil
- Accents: Azul slate, púrpura, tonos profesionales
- **Resultado:** Consonancia visual con dashboard, apariencia enterprise

---

## 📊 ARQUITECTURA ACTUAL

### Estructura HTML
```
body
├── .container (max-width: 420px)
│   ├── .header (orange gradient)
│   ├── .stats-bar
│   │   └── .stat-item (múltiples)
│   ├── .filter-tabs
│   │   └── .tab (múltiples, active/inactive)
│   ├── .challenges-container
│   │   ├── .featured-challenge
│   │   └── .challenge-card (múltiples)
│   │       ├── .challenge-header
│   │       ├── .challenge-title
│   │       ├── .challenge-description
│   │       ├── .challenge-meta
│   │       └── .challenge-actions
│   ├── .fab (Floating Action Button)
│   └── .bottom-nav (fixed footer nav)
└── .empty-state (when no challenges)
```

### CSS Variables (A Crear - Reutilizar del Dashboard)
```css
--color-primary: #4A90E2 (azul slate)
--color-primary-dark: #2E5C8A
--color-secondary: #7C3AED (púrpura)
--color-success: #10B981 (verde profesional)
--color-warning: #F59E0B (ámbar profesional)
--color-bg: #0F1419 (muy oscuro)
--color-bg-secondary: #1A1F2E (gris oscuro)
--color-bg-card: #1E2639 (azul-gris oscuro)
--color-bg-hover: #252E42
--color-text-dark: #E8EAED
--color-text-light: #A0A7B0
--color-text-muted: #6B7280
--color-border: #2D3748
--shadow-sm: 0 2px 8px rgba(0, 0, 0, 0.3)
--shadow-md: 0 5px 20px rgba(0, 0, 0, 0.4)
--shadow-lg: 0 10px 40px rgba(0, 0, 0, 0.5)
--transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1)
```

---

## 🔄 CAMBIOS POR SECCIÓN

### 1. BODY & CONTAINER
**Cambios:**
- Background: Light gradient → Dark gradient sofisticado
- Aplicar: `linear-gradient(135deg, #0A0E14 0%, #1A1F2E 25%, #2E2A3F 50%, #1A1F2E 75%, #0A0E14 100%)`
- `background-attachment: fixed`
- Container background: white → transparent (para que se vea el gradient)
- Container box-shadow: Actualizar para dark mode

### 2. HEADER
**Current:** Gradiente naranja (#ff6b35 → #f7931e)  
**Target:** Gris oscuro profesional con accent color  

**Cambios:**
- Background: `var(--color-bg-secondary)` o gradient sutil
- Eliminar o reposicionar el elemento `::before` decorativo
- Text color: Blanco/claro (`var(--color-text-dark)`)
- Button/link colors: Actualizar a primarios
- Mantener estructura y funcionamiento (back button, título, subtítulo)

### 3. STATS BAR
**Current:** Blanco, números naranjas  
**Target:** Dark background, números en color primario  

**Cambios:**
- Background: `var(--color-bg-card)`
- Border: `var(--color-border)`
- `.stat-number`: color `var(--color-primary)` (azul slate)
- `.stat-label`: color `var(--color-text-light)`

### 4. FILTER TABS
**Current:** White background, active naranja  
**Target:** Dark background, active con color primario  

**Cambios:**
- `.filter-tabs`: background `var(--color-bg-card)`, border `var(--color-border)`
- `.tab`: color `var(--color-text-light)`
- `.tab.active`: background `rgba(74, 144, 226, 0.1)`, color `var(--color-primary)`, border `var(--color-primary)`
- Remove border-bottom de inactive tabs, agregar bottom border a active

### 5. FEATURED CHALLENGE CARD
**Current:** Amarillo claro con borde naranja  
**Target:** Dark card con gradient overlay sutil  

**Cambios:**
- Background: `var(--color-bg-card)`
- Border: `1px solid var(--color-border)` (no 2px)
- Remove background gradient amarillo
- `.featured-badge`: background `var(--color-primary)`, text white
- Agregar subtle gradient overlay o glow effect

### 6. CHALLENGE CARDS
**Current:** Blanco con sombra sutil  
**Target:** Dark background con bordes y sombras profesionales  

**Cambios:**
- Background: `var(--color-bg-card)`
- Border: `1px solid var(--color-border)`
- Box-shadow: `var(--shadow-sm)`, hover: `var(--shadow-md)`
- Text color: `var(--color-text-dark)` (títulos), `var(--color-text-light)` (desc)

### 7. CHALLENGE STATUS BADGES
**Current:** Colores pastel brillantes  
**Target:** Colores sobrios profesionales  

**Cambios:**
- `.status-active`: background `rgba(16, 185, 129, 0.15)`, color `var(--color-success)`
- `.status-voting`: background `rgba(245, 158, 11, 0.15)`, color `var(--color-warning)`
- `.status-completed`: background `rgba(107, 114, 128, 0.15)`, color `var(--color-text-light)`

### 8. CHALLENGE CATEGORY TAGS
**Current:** Azul claro (#e3f2fd)  
**Target:** Dark background con color primario  

**Cambios:**
- Background: `rgba(74, 144, 226, 0.1)` o `var(--color-bg-hover)`
- Color: `var(--color-primary)`
- Border: 1px solid `var(--color-primary)`

### 9. VOTE BUTTONS
**Current:** White con bordes grises, hover naranja  
**Target:** Dark con color primario en hover/voted  

**Cambios:**
- Background: `transparent`
- Border: `1px solid var(--color-border)`
- Color: `var(--color-text-light)`
- `.vote-btn:hover`: border-color `var(--color-primary)`, background `rgba(74, 144, 226, 0.1)`
- `.vote-btn.voted`: background `var(--color-primary)`, border-color `var(--color-primary)`, color white
- `.vote-count`: color `var(--color-primary)`

### 10. ACTION BUTTONS (Comment, Share)
**Current:** Azules y verdes claros  
**Target:** Dark backgrounds con colores profesionales  

**Cambios:**
- `.btn-comment`: background `rgba(74, 144, 226, 0.1)`, color `var(--color-primary)`
- `.btn-share`: background `rgba(16, 185, 129, 0.1)`, color `var(--color-success)`

### 11. FLOATING ACTION BUTTON (FAB)
**Current:** Gradiente naranja  
**Target:** Gradiente azul slate → púrpura con shadow dark  

**Cambios:**
- Background: `linear-gradient(135deg, var(--color-primary) 0%, var(--color-secondary) 100%)`
- Box-shadow: `var(--shadow-lg)` con colores adaptados
- Color: White
- `.fab:hover`: usar `var(--transition)` para consistencia

### 12. FAB TOOLTIP
**Cambios:**
- Background: `var(--color-bg-secondary)`
- Color: `var(--color-text-dark)`
- Text-shadow: Opcional para mejor legibilidad

### 13. BOTTOM NAVIGATION
**Current:** Blanco con activo naranja  
**Target:** Dark background con activo en color primario  

**Cambios:**
- Background: `var(--color-bg-secondary)`
- Border-top: `1px solid var(--color-border)`
- `.nav-item.active`: background `rgba(74, 144, 226, 0.1)`, color `var(--color-primary)`
- `.nav-item:not(.active)`: color `var(--color-text-muted)`
- Agregar subtle shadow en top

### 14. EMPTY STATE
**Cambios:**
- `.empty-icon`: color `var(--color-text-muted)`
- `.empty-title`: color `var(--color-text-dark)`
- `.empty-description`: color `var(--color-text-light)`

### 15. RESPONSIVE & MEDIA QUERIES
**Cambios:**
- Adaptar dark mode para mobile breakpoints (380px)
- Mantener funcionalidad del container max-width
- Ajustar padding/margins para dark mode

---

## 🎨 PALETA DE COLORES FINAL

| Elemento | Current | Target | Hex |
|----------|---------|--------|-----|
| Header BG | Naranja gradiente | Gris oscuro | #1A1F2E |
| Card BG | Blanco | Azul-gris oscuro | #1E2639 |
| Featured Card BG | Amarillo claro | Azul-gris oscuro | #1E2639 |
| Primary accent | Naranja (#ff6b35) | Azul slate | #4A90E2 |
| Success | Verde (#2e7d32) | Verde profesional | #10B981 |
| Warning | Naranja (#ef6c00) | Ámbar profesional | #F59E0B |
| Stats number | Naranja (#ff6b35) | Azul slate | #4A90E2 |
| Text Dark | #2c3e50 | Gris claro | #E8EAED |
| Text Light | #555 | Gris medio | #A0A7B0 |
| Text Muted | #666 | Gris oscuro-medio | #6B7280 |
| Border | #e0e0e0 | Gris oscuro | #2D3748 |
| Background | Light gradient | Dark gradient | Ver CSS |
| FAB | Naranja gradiente | Azul-Púrpura | #4A90E2 → #7C3AED |

---

## 🚀 PLAN DE EJECUCIÓN

### FASE 1: CSS Variables & Body Background
- [ ] Crear/integrar sistema de CSS variables (reutilizar dashboard)
- [ ] Implementar dark gradient background en body
- [ ] Aplicar a container
- [ ] Actualizar box-shadow para dark mode

### FASE 2: Header & Stats Bar
- [ ] Rediseñar header a oscuro
- [ ] Remover/reposicionar decoraciones
- [ ] Actualizar stats bar styling
- [ ] Ajustar colores de números y labels

### FASE 3: Filter Tabs & Featured Card
- [ ] Actualizar filter tabs styling
- [ ] Rediseñar featured challenge card
- [ ] Ajustar featured badge colores
- [ ] Agregar gradient/glow effects

### FASE 4: Challenge Cards
- [ ] Actualizar challenge card backgrounds y bordes
- [ ] Ajustar status badges colores
- [ ] Actualizar category tags
- [ ] Refinar text colors y contraste

### FASE 5: Interactive Elements (Buttons, FAB, Nav)
- [ ] Rediseñar vote buttons
- [ ] Actualizar action buttons (comment, share)
- [ ] Cambiar FAB a gradiente azul-púrpura
- [ ] Actualizar bottom navigation styling

### FASE 6: Polish & Testing
- [ ] Empty state styling
- [ ] Media queries y responsive
- [ ] Validar contraste (WCAG AA)
- [ ] Testeo en navegador
- [ ] Animaciones en dark mode
- [ ] Commit y push a main

---

## ✅ CRITERIOS DE ACEPTACIÓN

1. **Visual Consistency**: Coherencia con dashboard + landing page + ruta del cambio modernizados
2. **Dark Mode**: Implementación completa sin elementos light legacy
3. **Professional**: Apariencia sobria y enterprise
4. **Accessibility**: Suficiente contraste y legibilidad
5. **Responsive**: Funciona correctamente en 380px, 320px, desktop
6. **Performance**: Sin impacto negativo en performance
7. **Color Accuracy**: Colores primarios y secundarios consistentes con sistema global

---

## 📝 NOTAS TÉCNICAS

- Mantener HTML structure intacta (cambios solo en CSS)
- Reutilizar variables CSS del dashboard y landing page
- Asegurar que animaciones (float, transitions) funcionen en dark mode
- Validar que emojis sean legibles en colores claros
- Mantener funcionalidad del FAB y bottom-nav
- Considerar agregar header profile/avatar (como en dashboard)
- El gradient background debe ser `background-attachment: fixed` para efecto de profundidad

---

## 🔗 REFERENCIAS

- Dashboard (ocp-puente-datos.html) - Sistema de colores establecido
- Ruta del Cambio (ruta-del-cambio-module.html) - Plan de ejecución similar
- Landing Page (index.html) - CSS Variables globales
- **Paleta Global:** #4A90E2 (primary), #7C3AED (secondary), #10B981 (success), #F59E0B (warning)
