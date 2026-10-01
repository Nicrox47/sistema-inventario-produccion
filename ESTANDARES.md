# Estándares del equipo
**Código de sesión: LLANO-14**

> **Estado de adopción:** las decisiones de proceso propuestas en esta versión fueron aceptadas por **Julian Camilo Caicedo Ramirez** y **Samuel Esteban Riveros Martinez** el 30 de septiembre de 2026.
>
> **Estado de entrega:** el código de sesión ya fue incorporado. Las decisiones del documento fueron aceptadas por ambos integrantes y este archivo se publica en el repositorio del equipo.

## 1. Identificación del proyecto

**Proyecto:** Sistema de inventario, recetas y planificación de producción.

**Propósito:** desarrollar una aplicación web que centralice inventario y recetas, calcule cuánto se puede producir con los ingredientes disponibles, permita planificar la producción por fecha y muestre reportes básicos de ventas.

**Alcance funcional principal:**

- Materias primas: existencias, entradas, salidas y materiales pendientes de llegada.
- Recetas y capacidad: ingredientes, cantidades, producción máxima, ingrediente limitante, recetas posibles y proyección con materiales por llegar.
- Planificación: producción por fecha, cantidad planeada, materiales requeridos, faltantes, registro de producción y descuento de insumos.
- Ventas y reportes: producto, cantidad, fecha, hora, reportes diarios, semanales y de hora pico.

**Restricción de proceso:** no se incorporan funciones fuera del alcance sin revisar su impacto sobre el tiempo disponible del equipo.

## 2. Integrantes y roles de la actividad

Integrantes confirmados:

- Julian Camilo Caicedo Ramirez.
- Samuel Esteban Riveros Martinez.

El Acta ya distribuye responsabilidades generales entre ambos. Para esta actividad se propone la siguiente asignación específica de los cuatro roles obligatorios:

| Rol de la actividad | Responsable | Función |
|---|---|---|
| Redactor | Samuel Esteban Riveros Martinez | Escribe y actualiza `ESTANDARES.md` únicamente a partir de acuerdos del equipo. |
| Guardián de lo verificable | Julian Camilo Caicedo Ramirez | Revisa que cada regla tenga una evidencia o comprobación objetiva. Si no puede comprobarse, solicita reescritura o eliminación. |
| Responsable del repositorio | Samuel Esteban Riveros Martinez | Crea/actualiza el archivo, prepara la rama y el commit, abre la revisión y comparte la evidencia del repositorio. |
| Abogado del diablo | Julian Camilo Caicedo Ramirez | Busca escenarios realistas en los que una regla sea imposible, ambigua o demasiado costosa y solicita ajustarla antes de adoptarla. |

> **Decisión adoptada por el equipo.** Ambos integrantes aprobaron esta distribución de roles.

## 3. Tecnologías y herramientas reales

### 3.1 Confirmadas por el Acta

| Tecnología / herramienta | Estado | Uso |
|---|---|---|
| HTML | Confirmada | Estructura de la interfaz web. |
| CSS | Confirmada | Estilos propios. |
| Bootstrap | Confirmada | Framework CSS/frontend para la interfaz. |
| JavaScript | Confirmada | Comportamiento del lado del cliente. |
| PHP | Confirmada | Lógica del lado del servidor. |
| MySQL | Confirmada | Persistencia de datos. |
| Git | Confirmada | Control de versiones. |
| GitHub | Confirmada | Repositorio y revisión del trabajo. |

**Framework backend:** las fuentes disponibles **no confirman ningún framework PHP**. No se documenta Laravel, Symfony ni otro framework como parte del proyecto mientras no exista evidencia en el repositorio.

### 3.2 Estado de verificación del repositorio

No se tuvo acceso al repositorio real durante la elaboración de esta versión. Por lo tanto, **no se afirman** ramas existentes, configuraciones, dependencias, versiones, hashes, historial ni archivos que no aparezcan en las fuentes.

Las herramientas de formato de la sección 4.3 son una **propuesta de adopción** y deben configurarse en el repositorio antes de exigir su comprobación automática.

## 4. Guía de estilo

### 4.1 Guías oficiales adoptadas

**Adoptado por el equipo:**

- **PHP:** PSR-12 como guía base de estilo.
- **JavaScript:** JavaScript Standard Style como guía base de estilo.
- **HTML y CSS:** formato automático con Prettier y convenciones de nombres definidas en este documento.

Estas guías no sustituyen las reglas específicas del dominio definidas aquí.

### 4.2 Idioma del código

**Adoptado por el equipo:** usar **español** para los nombres propios del dominio y para la documentación del proyecto.

Reglas:

- Variables: español.
- Funciones y métodos: español.
- Clases: español.
- Archivos creados por el equipo: español.
- Comentarios: español.
- Documentación: español.
- Nombres de librerías, palabras reservadas, API externas y conceptos técnicos estándar conservan el idioma definido por la herramienta.

No se permiten mezclas arbitrarias como `guardarUser()` o `deleteRegistro()`.

Convenciones generales:

- Variables y funciones: `camelCase`.
- Clases: `PascalCase`.
- Constantes: `MAYUSCULAS_CON_GUION_BAJO`.
- Archivos de páginas o scripts: `kebab-case`, por ejemplo `reporte-semanal.php`.
- Si un archivo representa una clase PHP, debe usar el mismo nombre que la clase, por ejemplo `CalculadoraProduccion.php`.

### 4.3 Formateador

Como el repositorio no estuvo disponible para verificar herramientas existentes, el equipo adopta los siguientes formateadores compatibles con el stack. **Su configuración en el repositorio aún debe realizarse o verificarse antes de exigirlos como control automático:**

#### PHP — PHP CS Fixer

Instalación propuesta, desde la raíz del repositorio:

```bash
composer require --dev friendsofphp/php-cs-fixer
```

Archivo de configuración a crear en la raíz: `.php-cs-fixer.php`

```php
<?php

$finder = PhpCsFixer\Finder::create()
    ->in(__DIR__)
    ->exclude(['vendor', 'node_modules']);

return (new PhpCsFixer\Config())
    ->setRules([
        '@PSR12' => true,
    ])
    ->setFinder($finder);
```

Comprobar formato sin modificar archivos:

```bash
vendor/bin/php-cs-fixer fix --dry-run --diff
```

Aplicar formato:

```bash
vendor/bin/php-cs-fixer fix
```

**Cumple** si el comando de comprobación termina sin proponer cambios.

#### JavaScript, HTML y CSS — Prettier

Instalación propuesta:

```bash
npm install --save-dev prettier
```

Archivo de configuración a crear en la raíz: `.prettierrc.json`

```json
{
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "useTabs": false
}
```

Comprobar formato:

```bash
npx prettier "**/*.{js,html,css}" --check
```

Aplicar formato:

```bash
npx prettier "**/*.{js,html,css}" --write
```

**Cumple** si el comando `--check` termina sin reportar archivos sin formatear.

> Las versiones exactas deben quedar fijadas por `composer.lock` y `package-lock.json` cuando estas herramientas se incorporen al repositorio. No se inventan versiones en este documento.

### 4.4 Reglas de nombres

Además de las convenciones generales, el equipo adopta estas tres reglas propias del dominio:

#### Regla 1 — Booleanos formulados como estado o pregunta comprobable

**Regla:** todo booleano debe comenzar con un prefijo que permita entender que su valor es verdadero/falso, por ejemplo `es`, `esta`, `tiene` o `puede`.

**Ejemplo correcto:** `tieneFaltantes`, `estaDisponible`, `puedeProducirse`.

**Ejemplo incorrecto:** `faltantes`, `disponibilidad`, `produccion`.

**Cómo verificarla:** revisar la declaración de variables, propiedades y retornos booleanos; el nombre debe expresar una condición binaria sin abrir el archivo que la consume.

#### Regla 2 — Funciones y métodos comienzan con un verbo

**Regla:** toda función o método creado por el equipo debe comenzar con un verbo en infinitivo que describa la acción.

**Ejemplo correcto:** `calcularProduccionMaxima()`, `registrarVenta()`, `obtenerIngredienteLimitante()`.

**Ejemplo incorrecto:** `produccionMaxima()`, `venta()`, `ingredienteLimitante()`.

**Cómo verificarla:** revisar los nombres de funciones y métodos modificados en el diff; cada uno debe comenzar con un verbo.

#### Regla 3 — La unidad aparece en el nombre cuando puede existir ambigüedad

**Regla:** si una cantidad o duración puede expresarse en más de una unidad, el nombre debe incluir la unidad utilizada.

**Ejemplo correcto:** `cantidadGramos`, `tiempoMinutos`, `pesoKilogramos`.

**Ejemplo incorrecto:** `cantidad`, `tiempo`, `peso`.

**Cómo verificarla:** revisar variables numéricas relacionadas con materias primas, recetas, tiempos o medidas; si la unidad no es inequívoca por el contexto inmediato, debe estar en el nombre.

## 5. Convención de commits

### 5.1 Formato

Se usa Conventional Commits con este formato:

```text
tipo(alcance): descripción
```

Reglas de la descripción:

- Debe estar en español.
- Debe comenzar con un verbo en imperativo.
- Debe describir un cambio concreto.
- Debe corresponder a un único cambio lógico.
- Debe evitar mensajes genéricos.

Ejemplo:

```text
feat(inventario): registra movimientos de entrada y salida
```

### 5.2 Tipos permitidos

| Tipo | Cuándo usarlo |
|---|---|
| `feat` | Nueva funcionalidad visible o nueva capacidad del sistema. |
| `fix` | Corrección de un defecto. |
| `docs` | Cambio exclusivamente documental. |
| `refactor` | Reorganización interna sin cambiar el comportamiento esperado. |
| `test` | Adición o modificación de pruebas o casos de verificación. |
| `style` | Cambio de formato que no altera la lógica. |
| `chore` | Configuración técnica o mantenimiento que no encaja en los tipos anteriores, por ejemplo configurar formateadores. |

### 5.3 Ejemplos

```text
feat(recetas): calcula la produccion maxima por ingredientes disponibles
fix(planificacion): corrige el calculo de faltantes por fecha
docs(estandares): documenta la politica de revision del equipo
refactor(ventas): separa el calculo de hora pico del registro de ventas
test(reportes): agrega casos para reporte diario y semanal
style(interfaz): aplica formato al formulario de materias primas
chore(herramientas): configura los formateadores del proyecto
```

### 5.4 Atomicidad y commits no aceptables

**Regla de atomicidad:** un commit representa **un cambio lógico identificable**. Si dos cambios pueden revisarse o revertirse de manera independiente, deben estar en commits separados.

Ejemplo correcto:

```text
feat(recetas): calcula el ingrediente limitante
```

Ejemplo incorrecto:

```text
feat(sistema): agrega inventario, corrige reportes y cambia estilos
```

No se aceptan mensajes como:

```text
cambios
arreglos
final
final2
ahora si
avance
cosas
prueba
```

## 6. Convención de ramas

**Adoptado por el equipo:** utilizar un esquema simple basado en `main`, `develop` y ramas cortas de trabajo.

| Rama | Uso | Regla de integración |
|---|---|---|
| `main` | Contiene versiones integradas y estables al cierre de cada sprint o entrega. | No recibe trabajo directo. Se actualiza desde `develop` mediante revisión. |
| `develop` | Rama de integración del sprint actual. | Recibe ramas de trabajo revisadas. |
| `feat/<hu>-<nombre-corto>` | Nueva historia o funcionalidad. | Se crea desde `develop`, se integra por Pull Request y se elimina después. |
| `fix/<nombre-corto>` | Corrección de un defecto. | Se crea desde `develop`, se integra por Pull Request y se elimina después. |
| `docs/<nombre-corto>` | Cambios exclusivamente documentales. | Se crea desde `develop`, se integra por Pull Request y se elimina después. |

Ejemplos:

```text
feat/hu04-produccion-maxima
feat/hu07-programar-produccion
fix/faltantes-por-fecha
docs/estandares-equipo
```

Reglas:

1. No se desarrolla directamente en `main`.
2. No se desarrolla directamente en `develop`, salvo una corrección mínima acordada por ambos para recuperar la integridad de la rama; si ocurre, debe quedar explicada en el commit.
3. Toda rama de trabajo nace desde `develop` actualizado.
4. Toda rama de trabajo se integra mediante Pull Request revisado por el otro integrante.
5. Después de integrar, la rama de trabajo se elimina.

## 7. Definition of Ready (DoR)

Una historia puede comenzar a desarrollarse solo cuando cumple **todas** las condiciones siguientes:

| # | Condición | Evidencia verificable |
|---|---|---|
| 1 | La historia está registrada con identificador, título, actor/necesidad y resultado esperado. | Registro de la HU en el backlog o issue del repositorio. |
| 2 | Tiene criterios de aceptación concretos y comprobables. | Lista de criterios en la misma HU/issue. |
| 3 | Las dependencias, datos y reglas de negocio necesarias están identificadas; cualquier dependencia bloqueante está resuelta o marcada explícitamente. | Sección de dependencias en la HU/issue y enlace o referencia al elemento correspondiente. |
| 4 | La historia tiene estimación y sprint asignado. | Estimación y sprint visibles en el backlog/issue. |
| 5 | Si modifica interfaz, existen campos, flujo o boceto suficiente para implementarla; si no aplica, se registra `No aplica`. | Boceto, captura, esquema o descripción adjunta/enlazada desde la HU. |
| 6 | Existe al menos un caso de prueba o ejemplo de entrada/salida que permita comprobar el resultado principal de la historia. | Caso documentado en la HU/issue con datos y resultado esperado. |

Si falta una de estas evidencias, la historia **no está Ready**.

## 8. Definition of Done (DoD)

Una implementación se considera lista para pasar a revisión únicamente cuando cumple todos los puntos aplicables de esta tabla. Un punto marcado "si aplica" solo puede omitirse dejando la razón escrita en la Pull Request.

| # | Condición | Dónde se verifica | Cómo se verifica | Cumple si |
|---|---|---|---|---|
| 1 | Todos los criterios de aceptación de la HU tienen un procedimiento reproducible de prueba. | HU/issue y Pull Request. | Otro integrante ejecuta los pasos con los datos indicados. | El resultado observado coincide con el resultado esperado en cada criterio. |
| 2 | Los archivos PHP modificados no tienen errores de sintaxis. | Archivos `.php` del diff. | Ejecutar `php -l <archivo>` para cada PHP modificado. | Cada comando termina con `No syntax errors detected`. |
| 3 | El flujo web afectado se ejecuta sin errores no controlados del cliente. | Página o módulo afectado. | Abrir el flujo en el navegador, ejecutar el caso principal y revisar la consola. | El flujo completa el resultado esperado y la consola no muestra errores JavaScript no controlados generados por el cambio. |
| 4 | El formato automático está conforme. | Archivos modificados. | Ejecutar los comandos `--dry-run/--check` de la sección 4.3. | Ambos comandos aplicables terminan sin proponer cambios. |
| 5 | Si el cambio modifica base de datos, el cambio queda representado en un archivo SQL versionado y reproducible; si no modifica BD, se registra `No aplica`. | Carpeta/archivo SQL definido por el repositorio y Pull Request. | Aplicar el SQL sobre una base de prueba compatible con el esquema anterior. | El script ejecuta sin error y deja disponible la estructura necesaria para la funcionalidad. |
| 6 | No se agregan credenciales, contraseñas, tokens ni datos sensibles al repositorio. | Diff de la Pull Request. | Revisar archivos nuevos y modificados, especialmente configuraciones. | No existen secretos en texto plano ni archivos locales de credenciales incluidos en el commit. |
| 7 | La documentación afectada está actualizada. | `README`, `ESTANDARES.md`, comentarios de configuración o documento correspondiente. | Comparar el comportamiento/configuración introducida con las instrucciones disponibles. | Un integrante nuevo puede ejecutar o usar el cambio siguiendo la documentación sin requerir una instrucción oral adicional. |

**Regla especial para cálculos de inventario, recetas y planificación:** cuando una HU incluya cantidades, unidades, producción máxima, ingrediente limitante, faltantes o descuento de insumos, el caso de prueba del punto 1 debe incluir valores de entrada y un resultado numérico conocido.

**Regla especial para reportes:** cuando una HU incluya reportes diarios, semanales u hora pico, el caso de prueba del punto 1 debe indicar el conjunto de ventas de prueba y el resultado esperado.

## 9. Política de revisión de código

### 9.1 Responsable de la revisión

Toda Pull Request es revisada por **el integrante distinto del autor**.

- Si Samuel es autor, revisa Julian.
- Si Julian es autor, revisa Samuel.

El autor no puede aprobar su propio cambio como única revisión.

### 9.2 Plazo

**Adoptado por el equipo:** la revisión debe realizarse en un máximo de **48 horas calendario** desde que la Pull Request queda marcada como lista para revisión.

Si el cierre del sprint ocurre antes de ese plazo, la revisión debe completarse antes de integrar el cambio en el cierre del sprint.

### 9.3 Causales de bloqueo

Un comentario se clasifica como **BLOQUEANTE** y debe resolverse antes de integrar cuando exista al menos una de estas situaciones:

- Un criterio de aceptación no se cumple.
- Falta una evidencia obligatoria de la DoD.
- Existe un error de lógica que produce cantidades, faltantes, producción máxima, descuentos de insumos o reportes incorrectos.
- El cambio rompe una funcionalidad existente directamente relacionada.
- Hay un error de sintaxis o un error JavaScript no controlado provocado por el cambio.
- Se incluyen credenciales, tokens, contraseñas o datos sensibles.
- Un cambio de base de datos requerido no queda reproducible desde el repositorio.
- El código o los nombres incumplen una regla obligatoria de este documento y el formateador no puede resolverla automáticamente.
- La Pull Request contiene más de un cambio lógico no relacionado que impide revisarla de forma independiente.

### 9.4 Situaciones que no bloquean

Se clasifican como **SUGERENCIA** y no impiden integrar:

- Preferencias personales cuando el código ya cumple el estándar.
- Refactors opcionales que no son necesarios para los criterios de aceptación.
- Mejoras futuras de interfaz no incluidas en la HU.
- Cambios cosméticos que el formateador ya resuelve.
- Optimizaciones de rendimiento no exigidas por el requisito actual y sin evidencia de un problema real.
- Ideas para ampliar el alcance que deben ir a otra HU.

### 9.5 Forma de comentar

Formato recomendado:

```text
[BLOQUEANTE] <problema concreto>. <evidencia o efecto>. <alternativa, si aplica>.
```

o:

```text
[SUGERENCIA] <mejora propuesta>. <motivo>.
```

Reglas de comunicación:

- El comentario se refiere al código, al requisito o al resultado, no a la persona.
- Debe indicar el problema concreto.
- Cuando sea posible, debe indicar cómo reproducirlo.
- Si existe una alternativa clara, puede proponerse.
- No se usan ataques personales ni comentarios ambiguos como "esto está mal" sin explicación.

### 9.6 Cierre de la revisión

La Pull Request puede integrarse cuando:

1. no existan comentarios **BLOQUEANTE** abiertos;
2. la DoD aplicable esté cumplida;
3. el revisor distinto del autor haya aprobado;
4. la rama esté actualizada respecto de `develop` o se hayan resuelto sus conflictos.

## 10. Flujo de trabajo resumido

```text
Historia preparada
        ↓
Cumple DoR
        ↓
Crear rama de trabajo desde develop
        ↓
Implementación
        ↓
Verificación DoD
        ↓
Pull Request y revisión por el otro integrante
        ↓
Corregir BLOQUEANTES, si existen
        ↓
Aprobación
        ↓
Integración en develop
        ↓
Eliminar rama de trabajo
        ↓
Al cierre del sprint, integrar develop en main
```

## 11. Aceptación de los estándares

La aceptación de ambos integrantes convierte en acuerdos del equipo las decisiones marcadas como propuestas de adopción en este documento.

- [x] **Julian Camilo Caicedo Ramirez** — **“conozco y acepto estos estándares”**
- [x] **Samuel Esteban Riveros Martinez** — **“conozco y acepto estos estándares”**

## 12. Declaración de apoyo de IA

Se utilizó una herramienta de inteligencia artificial como apoyo para organizar, redactar y revisar este documento a partir de las fuentes del proyecto y de los criterios de la actividad. El equipo es responsable de revisar el contenido, aprobar las decisiones de proceso y aceptar personalmente estos estándares.

**Código de sesión: LLANO-14**
