# Scripts Workflow

Скрипты и плагины очень полезные вещи, без них After Effects не был бы таким популярным. Рано или поздно коллекционирование скриптов превращается в интерфейс космического корабля.

![ui](Assets/scripts-kbar/ui.png)

Чтобы оптимизировать свой рабочий процесс, уменьшить количество панелей и дополнительное взаимодействие с ними, я использую известные экспрешены искрипты или пишу свои собственные. Сохраняю я их в коллекциях скриптов [Kbar2](https://aescripts.com/kbar/) и [moCode](https://aescripts.com/mocode/).

Главное правило таких кастомных скриптов, чтобы они выполнялись в один клик. То есть никаких всплывающих окон, дополнительных настроек и параметров. Одна кнопка скрипта выполняет конкретную одну функцию, или строго прописанный сценарий действий. Это позволяет значительно ускорить взаимодействие с интерфейсом, а еще можно назначить на такие скрипты шорткат и выполнять эти действия еще быстрее. Конечно есть несколько исключений, но их свожу к минимуму.

## Rename layers\Comps

Скрипт переименовывает группу свойств или слой, в зависимости от того что выбрано. Добавляет текст "handL" из переменной newShapeName к названию слоя, и добавляет нумерацию, если выделено несколько групп или слоев.

Также добавлен фильтр выделенных слоев. Если в переменной sortingType написано "shapes", то из всех выделенных слоев остаются только шейповые, иначе будут переименоваты все слои.

### Длинная форма

```javascript
app.beginUndoGroup('rename'); {
    var sortingType = "shapes";
    var newShapeName = "handL"
    var copyLayerName = true;
    var numbering = true;
    var sortingLayers = sortingInstance(sortingType);
    layerRename(newShapeName, sortingLayers, copyLayerName, numbering);
} app.endUndoGroup();

function layerRename(textImp, sortLay, copyLayerName, numbering){
    var textIter = "";
    var textPropIter = "";
    var layerName = "";
    var currentLayer;
    var newText = textImp;
    var filteredLayers = sortLay;
    for (var layerIter = 0; layerIter < filteredLayers.length ; layerIter++) {
        currentLayer = filteredLayers[layerIter];
        layerName = currentLayer.name;
        numbering == true ? textIter = "_" + (layerIter + 1) : textIter = "";
        var arrayProperty = currentLayer.selectedProperties;
        if (arrayProperty.length > 0){
            for (var propIter = 0; propIter < arrayProperty.length ; propIter++) {
                numbering == true ? textPropIter = "_" + (propIter + 1) : textPropIter = "";
                if (copyLayerName == true) {
                    arrayProperty[propIter].name = layerName + "_" + newText + textPropIter;
                } else {
                    arrayProperty[propIter].name += "_" + newText + textPropIter;
                }
            }
        } else {
            currentLayer.name = layerName + "_" + newText + textIter;  
        }
    };
}
function sortingInstance(inst){
    var instLayer = inst;
    var currentComp = app.project.activeItem;
    var arrayLayers = currentComp.selectedLayers;
    var sortingLayers = [];
    if (instLayer != "shapes") {
        for (var i in arrayLayers) {
            if (arrayLayers[i] instanceof ShapeLayer) sortingLayers.push(arrayLayers[i]);
        };
    } else{
        sortingLayers = arrayLayers;
    }
    return sortingLayers;
}
```

### Короткая форма с ограниченным функционалом

```javascript
app.beginUndoGroup('rename'); {
    var newText = "handL";
    var arrayLayers = app.project.activeItem.selectedLayers;
    for (var layerIter = 0; layerIter < arrayLayers.length ; layerIter++) {
        var currentLayer = arrayLayers[layerIter];
        var layerName = currentLayer.name;
        var arrayProperty = currentLayer.selectedProperties;
        if (arrayProperty.length > 0){
            for (var propIter = 0; propIter < arrayProperty.length ; propIter++) {
                arrayProperty[propIter].name = layerName + "_" + newText + "_" + (propIter + 1);
            }
        } else {
            currentLayer.name = layerName + "_" + newText + "_" + (layerIter + 1);  
        }
    }
} app.endUndoGroup();
```

## Compositions

## Shapes

## Nulls

## Animations

## Refs
