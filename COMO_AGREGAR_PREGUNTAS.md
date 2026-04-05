# 📖 Guía: Cómo Agregar Preguntas del PDF de USCIS

## ¿Qué se ha mejorado?

Tu aplicación ahora incluye:

✅ **Temporizador** - Muestra cuántos segundos tardaste en cada pregunta  
✅ **Auto-avance** - Si respondes correctamente, avanza automáticamente después de 1.5 segundos  
✅ **Retroalimentación visual** - Respuestas incorrectas en ROJO, correctas en VERDE  
✅ **Sonido en respuestas** - Los efectos de sonido se reproducen cuando seleccionas una respuesta  
✅ **Botón Siguiente** - Aparece después de respuesta incorrecta para que sigas cuando estés listo  
✅ **Menú de Inicio** - Botón para volver al menú en cualquier momento  
✅ **45 preguntas de civismo** - En español, listas para usar

## 📍 ¿Dónde están las preguntas?

Las preguntas están guardadas en el archivo:
```
us_civics_spanish.json
```

## 🔄 Cómo Agregar Más Preguntas del PDF

### Paso 1: Abre el archivo JSON
1. Ve a tu carpeta del proyecto
2. Abre `us_civics_spanish.json` con un editor de texto (Notepad++, VS Code, etc.)

### Paso 2: Entiende el formato
Cada pregunta sigue este patrón:

```json
{
  "id": 46,
  "block": "TEMA_PRINCIPAL",
  "question": "¿Tu pregunta en español aquí?",
  "correct": "A",
  "options": {
    "A": "La respuesta correcta",
    "B": "Opción falsa pero plausible",
    "C": "Otra opción falsa",
    "D": "Una opción más falsa"
  }
}
```

**Explicación:**
- **id**: Número único (incrementa: 46, 47, 48...)
- **block**: Categoría/tema (GOBIERNO, DERECHOS, HISTORIA, etc.)
- **question**: La pregunta en español
- **correct**: La letra de la respuesta correcta (A, B, C o D)
- **options**: Las 4 opciones de respuesta

### Paso 3: Extrae preguntas del PDF

1. **Abre el PDF**: `2025-Civics-Test-128-Questions-and-Answers.pdf`
2. **Lee una pregunta** del PDF
3. **Anota**:
   - La pregunta en inglés
   - La respuesta correcta del PDF
   - Las otras 3 opciones mostradas

### Paso 4: Traduce al español

Usa **Google Translate** o **DeepL** para traducir:
- La pregunta completa
- La respuesta correcta
- Las opciones falsas

**Consejo**: Mantén las traducciones claras y simples

### Paso 5: Crea opciones falsas inteligentes

Las opciones falsas deben:
- ✅ Sonar plausibles pero estar incorrectas
- ✅ No ser tan obvio que la respuesta correcta sea la única opción
- ✅ Incluir respuestas parcialmente correctas o similares
- ✅ Usar términos relacionados pero incorrectos

**Ejemplo bueno:**
```json
{
  "id": 46,
  "block": "PRESIDENTE",
  "question": "¿Cuántos términos puede servir un presidente?",
  "correct": "A",
  "options": {
    "A": "Máximo dos términos",
    "B": "Máximo tres términos",
    "C": "Ilimitado",
    "D": "Solo un término"
  }
}
```

### Paso 6: Agrega a un archivo de texto temporal

Crea un archivo llamado `nuevas_preguntas.txt` y escribe en JSON:

```json
[
  {
    "id": 46,
    "block": "CONGRESO",
    "question": "¿Cuál es la responsabilidad principal del Senado?",
    "correct": "B",
    "options": {
      "A": "Ejecutar las leyes",
      "B": "Aprobar o rechazar leyes",
      "C": "Interpretar la Constitución",
      "D": "Administrar los estados"
    }
  },
  {
    "id": 47,
    "block": "HISTORIA",
    "question": "¿Quién redactó principalmente la Declaración de Independencia?",
    "correct": "C",
    "options": {
      "A": "George Washington",
      "B": "Benjamin Franklin",
      "C": "Thomas Jefferson",
      "D": "John Adams"
    }
  }
]
```

### Paso 7: Copia y pega en el JSON principal

1. **Abre** `us_civics_spanish.json`
2. **Copia** las nuevas preguntas (sin los corchetes [ ] del principio/fin)
3. **Busca** el ÚLTIMO `}` antes del `]` final en el archivo
4. **Agrega** una coma después del último `}`
5. **Pega** todas las nuevas preguntas
6. **Guarda** el archivo

### Paso 8: Recarga la app

1. Abre el navegador a tu app (o presiona F5 para recargar)
2. Haz clic en "Comenzar Examen"
3. ¡Las nuevas preguntas estarán en el pool aleatorio de 20!

## ✅ Checklist para Cada Pregunta

Antes de agregar a JSON, verifica:

```
□ ¿La pregunta está clara en español?
□ ¿El "correct" es A, B, C o D?
□ ¿Todas las 4 opciones están presentes?
□ ¿No hay comas faltantes o extras?
□ ¿Incrementé el ID correctamente?
□ ¿El block tiene categoría válida?
□ ¿No hay caracteres especiales problema?
□ ¿El JSON es válido? (puedes probar en jsonlint.com)
```

## 🎯 Temas del PDF de USCIS

El PDF de USCIS cubre estos temas:

- **GOBIERNO** - Forma de gobierno, poderes
- **CONGRESO** - Senado, Cámara, números
- **PRESIDENTE** - Poderes, límites de términos
- **JUDICIAL** - Corte Suprema, jueces
- **DERECHOS** - Enmiendas, libertades
- **HISTORIA** - Independencia, Constitución
- **CIUDADANIA** - Derechos, deberes
- **GEOGRAFIA** - Estados, capitales, océanos
- **SIMBOLOS** - Bandera, águila

## 🐛 Solución de Problemas

**Problema**: "La aplicación dice No hay preguntas cargadas"
- **Solución**: Verifica que us_civics_spanish.json sea JSON válido (usa jsonlint.com)

**Problema**: "Las preguntas no aparecen después de editar"
- **Solución**: Presiona Ctrl+Shift+R (recarga fuerte) en el navegador

**Problema**: "Las nuevas preguntas no se mezclan"
- **Solución**: Esto es normal. El app elige 20 aleatorias cada vez

**Problema**: "Tengo un error de JSON"
- **Solución**: El archivo debe ser JSON válido. Verifica:
  - Comas después de cada `}` excepto el último
  - Comillas dobles alrededor de claves
  - Estructura anidada correcta

## 📚 Comandos SQL / VS Code útiles

**Para validar JSON en VS Code**:
1. Abre `us_civics_spanish.json`
2. Presiona F1
3. Escribe "JSON: Validate"

**Por línea de comando**:
```powershell
python -m json.tool us_civics_spanish.json
```

## 🎮 Prueba tu progreso

1. **Comienza el examen** desde tu app local
2. **Responde preguntas** - Verifica que el temporizador, sonidos y colores funcionen
3. **Obtén estadísticas** - Mira tu puntuación y tiempo promedio
4. **Reinicia** - Comprueba que se seleccionan nuevas preguntas aleatoriamente

## 📤 Sincroniza con GitHub (Avanzado)

Si quieres subir tus cambios a GitHub:

1. En VS Code, abre la Terminal (Ctrl+`)
2. Ejecuta:
```bash
git add -A
git commit -m "Agregué 20 nuevas preguntas de civismo"
git push origin main
```

¡Tu app se actualizará automáticamente en GitHub Pages!

---

## 💡 Consejos Pro

- 🔤 **Precisión en traducción**: Usa diccionarios de civismo para términos específicos
- 🎯 **Opciones falsas creíbles**: Incluye "trampas" que suenen correctas pero no lo sean
- 📊 **Distribución equilibrada**: Intenta tener preguntas de todos los temas
- 🔄 **Prueba multiplex**: Responde tu propio examen para verificar
- 💾 **Respaldo**: Guarda copias antes de cambios grandes

¡Éxito completando el examen de civismo! 🇺🇸
