# /create-branch

Crear una rama de git basada en el sistema de versionado del proyecto.

## Uso

```
/create-branch <TASK_ID>
```

Ejemplo: `/create-branch FLUX-108`

## Instrucciones

1. Leer el archivo `docs/VERSIONING.md` para obtener las convenciones de nombrado de ramas
2. Extraer el identificador de la tarea proporcionada (ej: `FLUX-108`)
3. Crear la rama siguiendo el formato definido en VERSIONING.md
4. Cambiar a la nueva rama

## Proceso

1. **Validar entrada**: Verificar que se proporcionó un ID de tarea válido
2. **Leer convenciones**: Consultar `docs/VERSIONING.md` para el formato de ramas
3. **Crear rama**: Ejecutar `git checkout -b <nombre-rama>` con el formato correcto
4. **Confirmar**: Mostrar la rama creada y su estado

## Notas

- Asegurarse de estar en la rama base correcta (main/develop) antes de crear la nueva rama
- Si VERSIONING.md define prefijos (feature/, bugfix/, hotfix/), usarlos según corresponda