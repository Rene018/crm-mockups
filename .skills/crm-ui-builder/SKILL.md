---
name: crm-ui-builder
description: >-
  CRM Extrucol UI builder — pages AND modals. ALWAYS USE when: create page, new screen,
  add modal, add dialog, design form, build layout, or any UI work in the CRM mockups.
  Trigger on: "nueva página", "nuevo modal", "crear pantalla", "diseñar", "agregar modal",
  "página de", "modal de", "formulario", "dashboard", "kanban", "table", "detail".
---

# CRM Extrucol UI Builder

Builds complete HTML pages and modals using the CRM Extrucol design system: tokens, components, icons, sidebar, and topbar.

## Quick Reference

### Page Skeleton
```html
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>CRM Extrucol · Rol · Page Name</title>
<link rel="stylesheet" href="../shared/tokens.css">
<link rel="stylesheet" href="../shared/components.css">
<style>
  /* Page-specific styles here */
</style>
</head>
<body>
<div style="display: flex; justify-content: center; background: #F4F4F5; padding: 40px;">
  <div style="width: 1440px;">
    <div class="app-shell" id="shell"></div>
  </div>
</div>
<script src="../shared/components.js"></script>
<script>
document.getElementById('shell').innerHTML = `
  ${renderSidebar('active-item-id', 'role-name')}
  <main class="main-area">
    ${renderTopbar({ title: 'Page Title', actions: '...' })}
    <div class="content">
      <!-- Page content -->
    </div>
  </main>
`;
// Page-specific JS
</script>
</body>
</html>
```

### Role Map
| Role | Sidebar param | Directory |
|------|--------------|-----------|
| Ejecutivo Comercial | `ejecutivo` | `ejecutivo/` |
| Coordinador | `coordinador` | `coordinador/` |
| Director | `director` | `director/` |
| Administrador | `admin` | `admin/` |

### Design Tokens (key values)
```
Primary:      #24388C   (--primary)
Accent:       #F39610   (--accent)
Success:      #1A8754   (--success)
Error:        #C0392B   (--error)
Surface:      #FFFFFF   (--surface)
Page BG:      #F7F7F7   (--page-bg)
Font:         Roboto (Google Fonts via tokens.css)
```

### Radii
`--radius-sm: 6px` · `--radius-md: 8px` · `--radius-lg: 12px` · `--radius-full: 9999px`

### Icon Usage
Access via `Icons` object (preloaded in components.js):
```
home, users, briefcase, clipboard, folder, chartBar, user, logout,
bell, search, filter, plus, pencil, trash, dots, close, chevronRight,
chevronDown, calendar, check, xCircle, arrowRight, download, clock,
building, coin, trophy, settings, clipboardCheck, flag, sparkles,
trendingUp, trendingDown, funnel, view, arrowsUpDown, currency,
chartPie, shieldCheck, adjustments, upload, database, globe, tag,
lock, gps, fire, inbox
```
Use: `${Icons.iconName}` in template strings.

---

## Page Layout Patterns

### Standard Page with Topbar
```html
<div class="content">
  <div class="page-head">
    <div class="page-head__title-group">
      <h1 class="page-head__title">Page Title</h1>
      <p class="page-head__subtitle">Optional subtitle</p>
    </div>
    <div class="page-head__actions">
      <button class="btn btn--primary">${Icons.plus} Nueva acción</button>
    </div>
  </div>
  <!-- Rest of content -->
</div>
```

### Stat Cards Row
```html
<div style="display: grid; grid-template-columns: repeat(4, 1fr); gap: 16px;">
  <div class="stat-card">
    <div class="stat-card__icon">${Icons.briefcase}</div>
    <div class="stat-card__label">Label</div>
    <div class="stat-card__value">42</div>
    <div class="stat-card__subtext">+2 this week</div>
  </div>
  <!-- repeat -->
</div>
```

### Kanban Board
```html
<div class="kanban kanban--4">
  <div class="kanban-col">
    <div class="kanban-col__header">
      <div class="kanban-col__dot" style="background: #3B82F6;"></div>
      <div class="kanban-col__label">Nuevo</div>
      <div class="kanban-col__count">8</div>
    </div>
    <div class="kanban-col__line" style="background: #3B82F6;"></div>
    <div class="kanban-col__list">
      <!-- kanban-card items -->
    </div>
  </div>
</div>
```

### Card Component
```html
<div class="card">
  <div class="card__header">
    <div class="card__title">Card Title</div>
    <button class="btn btn--ghost btn--sm">${Icons.plus} Add</button>
  </div>
  <div class="card__body">
    <!-- Card content -->
  </div>
  <div class="card__footer">
    <button class="btn btn--secondary">Cancelar</button>
    <button class="btn btn--primary">Guardar</button>
  </div>
</div>
```

### Table
```html
<div class="table-wrapper">
  <table class="table">
    <thead>
      <tr>
        <th>Columna 1</th>
        <th>Columna 2</th>
        <th>Acciones</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Data</td>
        <td>Data</td>
        <td><button class="table__action">${Icons.pencil}</button></td>
      </tr>
    </tbody>
  </table>
</div>
```

### Tabs
```html
<div class="tabs">
  <div class="tab is-active">Tab 1</div>
  <div class="tab">Tab 2 <span class="tab__count">3</span></div>
</div>
```

### Badges
```html
<span class="badge badge--prospecto"><span class="dot"></span>Prospecto</span>
<span class="badge badge--calificacion"><span class="dot"></span>Calificación</span>
<span class="badge badge--propuesta"><span class="dot"></span>Propuesta</span>
<span class="badge badge--negociacion"><span class="dot"></span>Negociación</span>
<span class="badge badge--ganada"><span class="dot"></span>Ganada</span>
<span class="badge badge--perdida"><span class="dot"></span>Perdida</span>
<span class="badge badge--info">Info</span>
<span class="badge badge--accent">Accent</span>
```

### Alert
```html
<div class="alert alert--info">${Icons.sparkles}<div>Message here</div></div>
<div class="alert alert--success">${Icons.check}<div>Success message</div></div>
<div class="alert alert--error">${Icons.warning}<div>Error message</div></div>
```

### Form Field Pattern
```html
<div class="form-field">
  <label class="form-field__label">Label <span class="req">*</span></label>
  <input class="input" placeholder="Placeholder" />
  <div class="form-field__hint">Hint text</div>
</div>

<div class="form-row">
  <div class="form-field">
    <label class="form-field__label">Field 1</label>
    <input class="input" />
  </div>
  <div class="form-field">
    <label class="form-field__label">Field 2</label>
    <select class="select">
      <option>Option 1</option>
      <option>Option 2</option>
    </select>
  </div>
</div>
```

### Avatar with Color Variants
```html
<div class="avatar avatar--color-1">JP</div>  <!-- blue #24388C -->
<div class="avatar avatar--color-2">MS</div>  <!-- purple #7C3AED -->
<div class="avatar avatar--color-3">LR</div>  <!-- green #1A8754 -->
<div class="avatar avatar--color-4">CO</div>  <!-- orange #C2410C -->
<div class="avatar avatar--color-5">AB</div>  <!-- sky #0369A1 -->
<div class="avatar avatar--color-6">DR</div>  <!-- amber #B45309 -->
<div class="avatar avatar--accent">EJ</div>   <!-- accent #F39610 -->

<!-- Sizes -->
<div class="avatar avatar--xs">S</div>
<div class="avatar avatar--sm">M</div>
<div class="avatar">O</div>       <!-- default 40px -->
<div class="avatar avatar--lg">L</div>
```

### Progress Bar
```html
<div class="progress">
  <div class="progress__bar">
    <div class="progress__fill" style="width: 72%;"></div>
  </div>
  <span style="font-size: 12px; font-weight: 600; color: var(--text-secondary);">72%</span>
</div>
```

### Timeline
```html
<div class="timeline">
  <div class="timeline__item">
    <div class="timeline__dot timeline__dot--success"></div>
    <div class="timeline__header">
      <div class="timeline__title">Actividad completada</div>
      <span class="timeline__date">Hoy, 10:30 AM</span>
    </div>
    <div class="timeline__desc">Descripción de la actividad.</div>
  </div>
</div>
```

### Activity Item
```html
<div class="activity-item">
  <div class="activity-item__dot activity-item__dot--blue"></div>
  <div class="activity-item__body">
    <div class="activity-item__title">Título <span class="badge badge--info">Nuevo</span></div>
    <div class="activity-item__desc">Descripción</div>
    <div class="activity-item__meta">
      <span>${Icons.calendar} 22 Abr 2026</span>
      <span>${Icons.user} Juan Pérez</span>
    </div>
  </div>
</div>
```

### Cliente Card
```html
<div class="cliente-card">
  <div class="cliente-card__header">
    <div class="avatar avatar--color-3">EM</div>
    <div>
      <div class="cliente-card__name">Empresa XYZ</div>
      <div class="cliente-card__company">NIT 900.123.456-1</div>
    </div>
  </div>
  <div class="cliente-card__info">
    <div class="cliente-card__info-row">${Icons.phone} (601) 234-5678</div>
    <div class="cliente-card__info-row">${Icons.envelope} contacto@empresa.com</div>
    <div class="cliente-card__info-row">${Icons.mapPin} Bogotá, Cundinamarca</div>
  </div>
  <div class="cliente-card__footer">
    <span>3 oportunidades activas</span>
    <span class="badge badge--ganada">Activo</span>
  </div>
</div>
```

---

## Modal Patterns

### Modal Overlay (base)
```css
.modal-overlay {
  position: absolute; inset: 0;
  background: rgba(26,26,26,0.5);
  display: flex; align-items: flex-start; justify-content: center;
  padding: 60px 24px;
  z-index: 100;
}
.modal-content {
  background: var(--surface);
  border-radius: 12px;
  max-width: 560px; width: 100%;
  box-shadow: 0 20px 50px rgba(0,0,0,0.15);
  overflow: hidden;
}
.modal-header {
  padding: 20px 24px;
  border-bottom: 1px solid var(--border);
  display: flex; align-items: center; justify-content: space-between;
}
.modal-header__icon {
  width: 40px; height: 40px;
  background: var(--success-bg); color: var(--success);
  border-radius: 10px; display: flex; align-items: center; justify-content: center;
  margin-right: 12px;
}
.modal-header__icon--error { background: var(--error-bg); color: var(--error); }
.modal-header__icon--accent { background: var(--accent-bg); color: var(--accent); }
.modal-body { padding: 20px 24px; }
.modal-footer {
  padding: 16px 24px; border-top: 1px solid var(--border);
  display: flex; justify-content: flex-end; gap: 10px;
  background: var(--page-bg);
}
```

### Modal Header Icon Types
| Type | BG | Color | Use for |
|------|----|----|---------|
| `--success` | `#E8F5EE` | `#1A8754` | Confirmations, conversions |
| `--error` | `#FDECEA` | `#C0392B` | Errors, destructive actions |
| `--accent` | `#FFF4E0` | `#C7770D` | Warnings, attention |

### Confirmation Modal (Success)
```html
<div class="modal-overlay">
  <div class="modal-content">
    <div class="modal-header">
      <div style="display: flex; align-items: center;">
        <div class="modal-header__icon">${Icons.trophy}</div>
        <div>
          <div style="font-weight: 700; font-size: 16px;">Título del modal</div>
          <div style="font-size: 12.5px; color: var(--text-muted);">Subtítulo explicativo</div>
        </div>
      </div>
      <button class="topbar__icon-btn">${Icons.close}</button>
    </div>
    <div class="modal-body">
      <!-- Content: form, info, preview -->
    </div>
    <div class="modal-footer">
      <button class="btn btn--secondary">Cancelar</button>
      <button class="btn btn--primary">${Icons.check} Confirmar acción</button>
    </div>
  </div>
</div>
```

### Form Modal (inside modal-body)
```html
<div class="form-field" style="margin-bottom: 12px;">
  <label class="form-field__label">Campo <span class="req">*</span></label>
  <input class="input" placeholder="Placeholder" />
</div>

<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 12px;">
  <div class="form-field">
    <label class="form-field__label">Campo 1</label>
    <select class="select"><option>Opción</option></select>
  </div>
  <div class="form-field">
    <label class="form-field__label">Campo 2</label>
    <input class="input" />
  </div>
</div>

<div class="alert alert--info">${Icons.sparkles}<div>Mensaje informativo.</div></div>
```

---

## Common Workflows

### Adding a Modal to a Page
Pages that show modals use `position: relative` on the wrapper:
```html
<div style="height: 900px; position: relative;">
  <div class="app-shell" id="shell"></div>
  <!-- modal-overlay sits here, outside shell -->
</div>
```

### Inline Modal (inside app-shell content)
```html
document.getElementById('shell').innerHTML = `
  ${renderSidebar('leads', 'ejecutivo')}
  <main class="main-area">
    ${renderTopbar({ title: 'Leads', actions: '...' })}
    <div class="content">
      <div class="modal-overlay">
        <div class="modal-content">
          <!-- modal content -->
        </div>
      </div>
    </div>
  </main>
`;
```

### Lead Card (Kanban)
```css
.lead-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 14px; box-shadow: var(--shadow-sm);
  cursor: grab; transition: all 180ms ease;
  display: flex; flex-direction: column; gap: 8px;
}
.lead-card:hover { border-color: var(--primary); box-shadow: var(--shadow-md); }
.lead-card__origen {
  display: inline-flex; align-items: center; gap: 4px;
  font-size: 10.5px; font-weight: 700; text-transform: uppercase;
  letter-spacing: 0.06em; color: var(--text-muted);
}
.lead-card__title { font-size: 13px; font-weight: 700; color: var(--text-primary); }
.lead-card__empresa { font-size: 11.5px; color: var(--text-muted); }
.lead-card__intereses { display: flex; flex-wrap: wrap; gap: 4px; margin-top: 2px; }
.lead-card__interes-chip {
  font-size: 10px; font-weight: 600; padding: 2px 7px;
  border-radius: 4px; background: var(--primary-bg); color: var(--primary);
}
.lead-card__footer {
  display: flex; align-items: center; justify-content: space-between;
  padding-top: 8px; border-top: 1px solid var(--border); margin-top: 2px;
}
.lead-card__score {
  display: inline-flex; align-items: center; gap: 3px;
  font-size: 11px; font-weight: 700; color: var(--accent);
}
.lead-card__age { font-size: 10.5px; color: var(--text-disabled); }
```

### Detail Header (Detail pages)
```css
.detail-header {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 20px 24px; margin-bottom: 16px;
}
.detail-header__row {
  display: flex; align-items: flex-start; gap: 16px; justify-content: space-between;
}
.detail-title {
  font-size: 22px; font-weight: 800; color: var(--text-primary);
  letter-spacing: -0.02em; line-height: 1.2;
}
.detail-subtitle { font-size: 13px; color: var(--text-muted); margin-top: 4px; }
.detail-meta {
  display: flex; gap: 24px; margin-top: 16px;
  padding-top: 16px; border-top: 1px solid var(--border); flex-wrap: wrap;
}
.detail-meta__item { display: flex; flex-direction: column; gap: 2px; }
.detail-meta__label {
  font-size: 10.5px; font-weight: 600; color: var(--text-disabled);
  text-transform: uppercase; letter-spacing: 0.06em;
}
.detail-meta__value { font-size: 14px; font-weight: 600; color: var(--text-primary); }
.detail-meta__value--accent { color: var(--accent); font-size: 17px; font-weight: 700; }
```

### Filter Bar
```html
<div class="filter-bar">
  <div class="input-wrapper">
    <span class="icon" style="position:absolute; left:12px; top:50%; transform:translateY(-50%);">${Icons.search}</span>
    <input class="input input--with-icon" placeholder="Buscar..." />
  </div>
  <button class="btn btn--secondary btn--sm">${Icons.filter} Filtros</button>
  <button class="btn btn--secondary btn--sm">${Icons.arrowsUpDown} Ordenar</button>
</div>
```

### Empty State
```html
<div class="empty-state">
  <div class="empty-state__icon">${Icons.inbox}</div>
  <div class="empty-state__title">Sin datos</div>
  <div class="empty-state__desc">Aquí aparecerán los elementos cuando los agregues.</div>
  <button class="btn btn--primary">${Icons.plus} Agregar primero</button>
</div>
```

### Loading
```html
<div class="loading">
  <div class="loading__spinner"></div>
  <span>Cargando...</span>
</div>
```

---

## File Naming

Pages: `{XX}-{page-slug}.html` in the appropriate role directory.
Modal examples inside pages don't need separate files.

| Role | Path |
|------|------|
| Ejecutivo | `ejecutivo/{XX}-{slug}.html` |
| Coordinador | `coordinador/{XX}-{slug}.html` |
| Director | `director/{XX}-{slug}.html` |
| Admin | `admin/{XX}-{slug}.html` |
| Auth | `auth/{XX}-{slug}.html` |

---

## Steps to Create a New Page

1. Identify role directory and next sequence number
2. Create the HTML file from Page Skeleton
3. Use `renderSidebar('active-id', 'role')` with correct active item ID
4. Use `renderTopbar({ title, breadcrumb, actions })` for the topbar
5. Apply component classes from Quick Reference above
6. Add page-specific CSS in `<style>` block if needed
7. Add JS data and render functions
8. Open in browser to verify

## Steps to Add a Modal

1. Add modal CSS to page `<style>` (use Modal base CSS)
2. Choose modal type: Confirmation, Form, or Conversion
3. Build the modal HTML structure
4. Place `modal-overlay` in correct position (inline or wrapper-relative)
5. Wire close button and action buttons

## State Colors (Kanban / Badges)
| State | Badge Class | Dot/BG |
|-------|-------------|--------|
| Nuevo | `prospecto` | `#EEF1FA` / `#24388C` |
| Contactado | `propuesta` | `#F3E8FF` / `#7C3AED` |
| Interesado | `calificacion` | `#FFF4E0` / `#C7770D` |
| Negociación | `negociacion` | `#FEF9C3` / `#A16207` |
| Ganada | `ganada` | `#E8F5EE` / `#1A8754` |
| Perdida | `perdida` | `#FDECEA` / `#C0392B` |
