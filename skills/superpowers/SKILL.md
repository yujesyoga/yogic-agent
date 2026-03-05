# Superpowers — Desarrollo estructurado con sub-agentes

Adaptado de [obra/superpowers](https://github.com/obra/superpowers) + [elcano-superpowers](https://clawhub.ai/skills/elcano-superpowers).

## Cuándo activar

Cuando el usuario pida una **feature nueva, refactor grande o cambio multi-archivo**. NO para fixes de una línea o cambios cosméticos — esos se resuelven directo.

## El flujo

```
1. BRAINSTORM → 2. PLAN → 3. EXECUTE → 4. REVIEW → 5. SHIP
```

---

## 1. BRAINSTORM

**HARD GATE: No escribir código hasta tener diseño aprobado.**

Aunque parezca simple. Las asunciones son donde los proyectos mueren.

### Pasos:
1. **Explorar** — leer archivos relevantes, commits recientes, estado actual
2. **Preguntar** — una pregunta a la vez, preferir opciones múltiples
3. **Proponer 2-3 enfoques** — con trade-offs y recomendación
4. **Presentar diseño** — en secciones digeribles, esperar OK antes de avanzar
5. **Guardar** — `docs/plans/YYYY-MM-DD-<feature>-design.md`

### Qué cubrir:
- Arquitectura / componentes afectados
- Flujo de datos
- Manejo de errores
- Cómo se testea
- Impacto en lo existente

---

## 2. PLAN

Después del diseño aprobado, plan de implementación granular.

### Reglas:
- Guardar en `docs/plans/YYYY-MM-DD-<feature>-plan.md`
- Cada tarea = **2-5 minutos** de trabajo
- **Paths exactos** de archivos a crear/modificar
- **Código completo** en el plan (no "añadir validación")
- **Comandos exactos** con output esperado
- DRY, YAGNI, commits frecuentes

### Estructura de tarea:

```markdown
### Tarea N: [Nombre]

**Archivos:**
- Crear: `ruta/exacta/archivo.ts`
- Modificar: `ruta/exacta/existente.ts`

**Paso 1:** Test que falle → [código completo]
**Paso 2:** Verificar: `npm test -- --grep "nombre"` → FAIL
**Paso 3:** Implementación mínima → [código completo]
**Paso 4:** Verificar: `npm test -- --grep "nombre"` → PASS
**Paso 5:** `git add ... && git commit -m "feat: descripción"`
```

### Al terminar el plan, preguntar:
> "Plan guardado en `docs/plans/...`. ¿Ejecuto con sub-agentes o prefieres revisarlo primero?"

---

## 3. EXECUTE — Sub-agente por tarea

Un `sessions_spawn` por tarea. Contexto fresco = sin contaminación.

### Prompt del sub-agente implementador:

```
Eres un implementador. Tu ÚNICA tarea es ejecutar exactamente lo que dice el plan.

REGLAS:
- Sigue el plan al pie de la letra
- Si algo no está claro, PARA y pregunta — no improvises
- Test primero, implementación después
- Commit al terminar
- NO hagas nada fuera del plan

TAREA:
[texto completo de la tarea]

CONTEXTO:
[archivos relevantes, stack, convenciones]
```

### Doble review por tarea:

**Review 1: Spec compliance**
- ¿Se crearon/modificaron los archivos correctos?
- ¿Los tests pasan?
- ¿Se añadió algo fuera del plan? → revertir
- ¿Falta algo del plan? → completar

**Review 2: Calidad**
- ¿El código es limpio y legible?
- ¿Los tests cubren edge cases?
- ¿Hay code smells?

Si falla un review → nuevo sub-agente con feedback específico. Re-review hasta aprobar.

---

## 4. REVIEW FINAL

- Build pasa sin errores
- Screenshot/verificación si hay UI
- Review del diff total
- Documentar en daily notes

---

## 5. SHIP

- `git push`
- Restart del proceso si aplica
- Notificar al usuario con resumen

---

## Principios (Niyamas del código)

| Sánscrito | Técnico | Significado |
|-----------|---------|-------------|
| Ahiṃsā | No hacer daño | No introducir deuda técnica innecesaria |
| Satya | Verdad | Evidence over claims — verificar antes de declarar victoria |
| Aparigraha | No acumular | YAGNI — no construir lo que no se pidió |
| Śauca | Limpieza | DRY — código limpio y sin repetición |
| Tapas | Disciplina | TDD — test primero, siempre |

**El plan es ley.** Si hay que desviarse, parar y re-planificar con el usuario.
