# 📋 PLAN DE MEJORA - RUTA DEL CAMBIO MODULE
**Fecha:** 25 de Marzo, 2026  
**Estado:** En Planificación  
**Objetivo:** Modernizar diseño de "Ruta del Cambio" a Dark Theme + Sobrio Professional

---

## 🎯 OBJETIVOS GENERALES

### Current State (Light Theme)
- Header: Gradiente verde (#27ae60 → #2ecc71)
- Background: Light gradient (#f0f4f8 → #e8f5e8)
- Cards: Blanco con bordes sutiles
- Timeline: Colores verdes y naranjas brillantes
- Accents: Verde, naranja, gris claros
- **Problema:** Diseño "infantil" y poco profesional, inconsistente con el dashboard modernizado

### Target State (Dark Theme + Professional)
- Header: Gris oscuro profesional
- Background: Dark gradient sofisticado con fade (similar a dashboard)
- Cards: Dark backgrounds (#1E2639) con bordes sutiles
- Timeline: Colores sobrios profesionales
- Accents: Azul slate, púrpura, tonos profesionales
- **Resultado:** Consonancia visual con dashboard, apariencia enterprise

---

## 📊 ARQUITECTURA ACTUAL

### Estructura HTML
```
body
├── .container (max-width: 420px)
│   ├── .header (green gradient)
│   ├── .project-selector
│   ├── .timeline-container
│   │   ├── .overall-progress
│   │   └── .timeline
│   │       └── .timeline-step (múltiples)
│   │           ├── .step-indicator
│   │           └── .step-card
│   └── .bottom-nav (fixed footer nav)
```

### CSS Variables (A Crear)
```css
--color-primary: #4A90E2 (azul slate)
--color-primary-dark: #2E5C8A
--color-secondary: #7C3AED (púrpura)
--color-success: #10B981 (verde profesional)
--color-warning: #F59E0B (ámbar profesional)
--color-bg: #0F1419 (muy oscuro)
--color-bg-secondary: #1A1F2E (gris oscuro)
--color-bg-card: #1E2639 (azul-gris oscuro)
--color-text-dark: #E8EAED
--color-text-light: #A0A7B0
--color-border: #2D3748
```

---

## 🔄 CAMBIOS POR SECCIÓN

### 1. BODY & CONTAINER
**Cambios:**
- Background: Light gradient → Dark gradient sofisticado (similar a dashboard)
- Aplicar: `linear-gradient(135deg, #0A0E14 0%, #1A1F2E 25%, #2E2A3F 50%, #1A1F2E 75%, #0A0E14 100%)`
- `background-attachment: fixed`

### 2. HEADER
**Current:** Verde gradiente (#27ae60 → #2ecc71)  
**Target:** Gris oscuro profesional con accent color  

**Cambios:**
- Background: `var(--color-bg-secondary)`
- Cambiar padding/altura en función del nuevo diseño
- Actualizar colores de texto a claros
- Mantener estructura de contenido (back button, título, subtítulo)
- Remover/Actualizar emoji del título

### 3. PROJECT SELECTOR
**Current:** Bordes grises, background blanco  
**Target:** Dark mode professional  

**Cambios:**
- Background: `var(--color-bg-card)`
- Borders: `var(--color-border)`
- Text colors: Light text on dark
- Label color: `var(--color-text-light)`
- Dropdown: Dark with primary color hover state

### 4. TIMELINE MAIN CONTAINER
**Cambios:**
- Padding: Actualizar para dark mode
- Background: Heredar del body

### 5. PROGRESS BAR SECTION
**Current:**
- Container BG: Blanco
- Bar fill: Verde gradiente (#27ae60 → #2ecc71)
- Badge: verde background

**Target:**
- Container BG: `var(--color-bg-card)`
- Bar fill: Gradient primario sofisticado
- Badge: Colores profesionales

**Cambios específicos:**
- `.overall-progress`: background `var(--color-bg-card)`, border `var(--color-border)`
- `.progress-bar-fill`: Gradient azul-slate → púrpura
- `.progress-percentage`: `var(--color-primary)` background
- Text colors: Actualizar a claros

### 6. TIMELINE VISUAL
**Current:**
- Línea vertical: Verde → gris
- Indicador (círculo): Verde (completado), Naranja (activo), Gris (pending)

**Target:**
- Línea vertical: Gradiente `var(--color-primary)` → `var(--color-border)`
- Indicadores:
  - Completado: `var(--color-success)`
  - Activo: `var(--color-warning)` con pulse animation
  - Pending: `var(--color-border)`

### 7. STEP CARDS
**Current:**
- Background: Blanco con colores tintados
- Border-left: Colores brillantes
- Box-shadow: Ligero

**Target:**
- Base background: `var(--color-bg-card)`
- Border-left:
  - Completado: `var(--color-success)` (#10B981)
  - Activo: `var(--color-warning)` (#F59E0B)
  - Pending: `var(--color-border)`
- Text: Claros sobre fondo oscuro
- Box shadows: Oscuros adaptados

**Cambios específicos:**
```css
.step-card {
  background: var(--color-bg-card)
  border: 1px solid var(--color-border)
  color: var(--color-text-dark)
  box-shadow: 0 2px 8px rgba(0,0,0,0.3)
}
```

### 8. STATUS BADGES
**Current:** Colores pastel brillantes  
**Target:** Colores sobrios profesionales  

**Cambios:**
- `.status-completed`: Verde sofisticado con texto claro
- `.status-active`: Ámbar/naranja sofisticado
- `.status-pending`: Gris oscuro

### 9. TASK LIST
**Current:** Checkboxes grises/verdes  
**Target:** Checkboxes con colores profesionales  

**Cambios:**
- Task item color: `var(--color-text-light)`
- Checkbox border: `var(--color-border)`
- Checkbox filled: `var(--color-success)`

### 10. ACTION BUTTONS
**Current:**
- Primary: Verde (#27ae60)
- Secondary: Gris claro
- Upload: Azul

**Target:**
- Primary: `var(--color-primary)` con hover sofisticado
- Secondary: `var(--color-bg-hover)` con border sutil
- Upload: Actualizar al primario

**Cambios:**
- Add shadows for depth
- Update hover states for dark mode
- Consistent with dashboard buttons

### 11. BOTTOM NAVIGATION
**Current:** Blanco con verde highlight  
**Target:** Dark mode professional  

**Cambios:**
- Background: `var(--color-bg-secondary)`
- Border-top: `var(--color-border)`
- Nav-item active: `var(--color-primary)` background/text
- Nav-item inactive: `var(--color-text-muted)`

### 12. RESPONSIVE & MEDIA QUERIES
**Cambios:**
- Adaptar dark mode para mobile breakpoints
- Mantener funcionalidad del container max-width

---

## 📋 COMPONENTES SECUNDARIOS

### Back Button
- Current: Texto claro en header verde
- Target: Texto claro en header oscuro con hover effect

### Icons/Emojis
- Mantener emojis si es posible
- Considerar remover si afecta profesionalismo

### Animations
- Mantener pulse animation en active indicator
- Asegurar que funcionen en dark mode

---

## 🎨 PALETA DE COLORES FINAL

| Elemento | Current | Target | Hex |
|----------|---------|--------|-----|
| Header BG | Verde gradiente | Gris oscuro | #1A1F2E |
| Card BG | Blanco | Azul-gris oscuro | #1E2639 |
| Primary accent | Verde (#27ae60) | Azul slate | #4A90E2 |
| Success | Verde (#27ae60) | Verde sofisticado | #10B981 |
| Warning | Naranja (#f39c12) | Ámbar sofisticado | #F59E0B |
| Text Dark | #2c3e50 | Gris claro | #E8EAED |
| Text Light | #666 | Gris medio | #A0A7B0 |
| Border | #e0e0e0 | Gris oscuro | #2D3748 |
| Background | Light gradient | Dark gradient | Ver CSS |

---

## 🚀 PLAN DE EJECUCIÓN

### FASE 1: CSS Variables & Body
- [ ] Crear sistema de CSS variables (similar a dashboard)
- [ ] Implementar dark gradient background
- [ ] Aplicar a body y container

### FASE 2: Header & Project Selector
- [ ] Rediseñar header a oscuro
- [ ] Actualizar project selector styling
- [ ] Ajustar colores de texto y bordes

### FASE 3: Progress & Timeline
- [ ] Actualizar overall-progress card
- [ ] Modificar progress bar colors
- [ ] Rediseñar timeline visual (línea y indicadores)

### FASE 4: Step Cards
- [ ] Actualizar step-card backgrounds y borders
- [ ] Ajustar status badges
- [ ] Refinar task list styling

### FASE 5: Buttons & Navigation
- [ ] Rediseñar action buttons
- [ ] Actualizar bottom-nav
- [ ] Implementar hover effects para dark mode

### FASE 6: Polish & Testing
- [ ] Media queries y responsive
- [ ] Validar contraste (WCAG AA)
- [ ] Testeo en navegador
- [ ] Commit y push a main

---

## ✅ CRITERIOS DE ACEPTACIÓN

1. **Visual Consistency**: Coherencia con dashboard modernizado
2. **Dark Mode**: Implementación completa sin elementos light legacy
3. **Professional**: Apariencia sobria y enterprise
4. **Accessibility**: Suficiente contraste y legibilidad
5. **Responsive**: Funciona correctamente en mobile
6. **Performance**: Sin impacto negativo en performance

---

## 📝 NOTAS TÉCNICAS

- Mantener HTML structure intacta (cambios solo en CSS)
- Reutilizar variables CSS del dashboard donde sea posible
- Asegurar que animations funcionen en dark mode
- Validar que emojis sean legibles en colores claros
- Considerar agregar avatar/profile button al header (como en dashboard)

