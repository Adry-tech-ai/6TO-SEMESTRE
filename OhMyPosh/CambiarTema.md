# COMO CAMBIAR EL TEMA EN UBUNTU

## 1. Descarga el tema nuevo:
```
wget -O ~/.poshthemes/aliens.omp.json https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/[TEMA_NUEVO].omp.json
```

## 2. Comprueba que existe:
```
ls -l ~/.poshthemes/aliens.omp.json
```

## 3. Pruébalo:
```
eval "$(oh-my-posh init bash --config ~/.poshthemes/[TEMA_NUEVO].omp.json)"
``` 
---
## 4. Hazlo permanente:
### Entra al bash:
```
nano ~/.bashrc
```


### Cambia al nuevo tema:
```
# Oh My Posh - ALIENS
eval "$(oh-my-posh init bash --config ~/.poshthemes/aliens.omp.json)"
```
- Guarda Ctrl + O
- Enter
- Sal con Ctrl + X

### Aplica el cambio:
```
source ~/.bashrc
```
