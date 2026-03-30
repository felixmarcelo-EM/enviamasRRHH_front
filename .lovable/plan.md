

## Plan: Modal de Registrar Activo en Módulo de Activos y Equipos

### Objetivo
Agregar un Dialog/modal al botón "Registrar Activo" con un formulario para registrar nuevos equipos y asignarlos a empleados.

### Cambio único en `src/pages/AssetsPage.tsx`

1. **Nuevos estados**: `showRegistrar` (boolean), campos del formulario (`tipo`, `descripcion`, `empleado`, `marca`, `modelo`, `serie`, `estado`), y lista dinámica de activos con `useState`
2. **Dialog con formulario**:
   - **Tipo de activo** (Select): Laptop, Monitor, Headset, Teclado, Mouse, Otro
   - **Marca** (Input)
   - **Modelo / Descripción** (Input)
   - **Número de serie** (Input)
   - **Empleado asignado** (Select): lista mock de empleados + opción "Sin asignar"
   - **Estado** (Select): En uso, Asignado, En mantenimiento, Disponible
   - **Fecha de asignación**: automática (fecha actual) o seleccionable
   - **Observaciones** (Textarea, opcional)
3. **Al guardar**: agregar el activo a la lista local, cerrar modal, mostrar toast de confirmación
4. **Botón** → `onClick={() => setShowRegistrar(true)}`

### Imports adicionales
- `Dialog, DialogContent, DialogHeader, DialogTitle, DialogFooter`
- `Label`, `Textarea`
- `useToast` / `toast` de sonner
- `format` de `date-fns`

