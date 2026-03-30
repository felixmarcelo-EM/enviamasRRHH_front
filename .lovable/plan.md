

## Plan: Habilitar subida de foto en Nuevo Empleado

### Problema
El botón "Subir foto" no abre el explorador de archivos porque no tiene un `<input type="file">` asociado.

### Solución
En `src/pages/NewEmployeePage.tsx`:

1. Agregar un `useRef` para un input file oculto (`accept="image/*"`)
2. Al hacer clic en "Subir foto", disparar `inputRef.current.click()`
3. Agregar estado `fotoPreview` con `useState<string | null>` para almacenar la URL de preview via `URL.createObjectURL`
4. Mostrar la imagen en el círculo cuando exista preview, reemplazando el ícono Upload
5. Agregar botón "Quitar" cuando haya foto cargada

### Cambio único en `src/pages/NewEmployeePage.tsx`
- Agregar `useRef` + `useState` para el file input y preview
- Input oculto: `<input type="file" accept="image/*" ref={fileInputRef} onChange={handlePhotoChange} className="hidden" />`
- onClick del botón → `fileInputRef.current?.click()`
- En el círculo: si hay preview, mostrar `<img>` con `object-cover rounded-full`; si no, mostrar el ícono Upload

