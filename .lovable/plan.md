

## Plan: Modal de Nueva Solicitud en Portal del Empleado

### Objetivo
Agregar un Dialog al botón "Nueva Solicitud" en la pestaña Solicitudes del Portal del Empleado, permitiendo crear solicitudes de tipo: Falta, Tardanza, Salida Temprana o Vacaciones, cada una con campos adaptados.

### Cambio único en `src/pages/EmployeePortalPage.tsx`

1. **Nuevos estados**: `showNuevaSolicitud`, `tipoSolicitud`, `fechaInicio`, `fechaFin`, `justificacion`, y lista dinámica `solicitudes`
2. **Dialog con formulario dinámico**:
   - **Tipo de solicitud** (Select): Falta, Tardanza, Salida Temprana, Vacaciones
   - **Campos comunes**: Fecha (date picker)
   - **Campos condicionales por tipo**:
     - *Falta*: Fecha + Justificación (textarea obligatoria)
     - *Tardanza*: Fecha + Hora de llegada (input time) + Justificación
     - *Salida Temprana*: Fecha + Hora de salida (input time) + Justificación
     - *Vacaciones*: Fecha inicio + Fecha fin + Observaciones (textarea opcional) + cálculo automático de días
3. **Al guardar**: agregar a la tabla con estado "Pendiente", cerrar modal, toast de confirmación
4. **Botón** → `onClick={() => setShowNuevaSolicitud(true)}`

### Imports adicionales
- `Dialog, DialogContent, DialogHeader, DialogTitle, DialogFooter` de `@/components/ui/dialog`
- `Input`, `Label`, `Textarea`, `Select/SelectContent/SelectItem/SelectTrigger/SelectValue`
- `Calendar`, `Popover` para date pickers
- `useToast`, `useState`
- `format`, `differenceInCalendarDays` de `date-fns`

