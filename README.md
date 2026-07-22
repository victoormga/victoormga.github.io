# victoormga.github.io

Portfolio de Victor Garcia. Desplegado en GitHub Pages desde la rama `main`.

## Flujo de trabajo entre entornos

Este repo se edita desde dos entornos locales distintos. Para evitar conflictos:

### Antes de empezar a trabajar (siempre)

```bash
git checkout main
git pull origin main
```

Esto trae los ultimos cambios que se hayan subido desde el otro entorno.

### Despues de hacer cambios

```bash
git add -A
git commit -m "Descripcion del cambio"
git push origin main
```

### Si usas una rama auxiliar (ej. mejoras-portfolio)

Para integrar cambios de una rama a main:

```bash
git checkout main
git pull origin main
git merge mejoras-portfolio
git push origin main
```

Una vez mergeada, borrar la rama para evitar confusion:

```bash
git branch -d mejoras-portfolio
git push origin --delete mejoras-portfolio
```

### Reglas para evitar problemas

1. Nunca trabajar sin hacer `git pull` primero.
2. No copiar archivos manualmente entre ramas; usar `git merge`.
3. Si aparece `index.lock`, borrarlo antes de continuar: `del .git\index.lock` (Windows) o `rm .git/index.lock` (Linux/Mac).
4. GitHub Pages solo despliega `main`. Los cambios en otras ramas no se ven en el .io hasta hacer merge + push a main.
