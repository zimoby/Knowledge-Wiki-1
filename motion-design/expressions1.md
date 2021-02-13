# Expressions Part 1

По мере увеличения опыта работы в любом софте, мы начинаем сталкиваться с их ограничениями, которые не решаются простыми базовыми манипуляциями с интерфейсом. Это ограничения самого дизайна софта. В большинстве случае в редакторах компьютерной графики есть встроенный язык программирования расширяющий возможности. Экспрешены одни из таких решений.

Экспрешены нужны для

- Автоматизации анимации
- Рандомизации значений
- Создание сложных взаимосвязей для создания сетапов и ригов

## Links

- [Top 3 After Effects Expressions to Simplify Your Workflow](https://blog.motiondesign.school/top-3-after-effects-expressions)
- [4 Advanced After Effects Expressions Made Easy](https://blog.motiondesign.school/4-advanced-after-effects-expressions)

## Randomizers

### Wiggle

{% tabs %} {% tab title="Wiggle Short" %}

```javascript
wiggle(1, 20);
```

{% endtab %}

{% tab title="Wiggle Long" %}

```javascript
freq = 1
amp = 20;
wiggle(freq, amp);
```

{% endtab %}

{% tab title="Wiggle Randomize" %}

```javascript
freq = 1
amp = 20;
seed = 1;
seedRandom(seed, false);
wiggle(freq, amp);
```

{% endtab %} {% endtabs %}

### Пространственные преобразования

- toComp(value)
- layer.toComp[0,0,0] [The Making of TANK](https://youtu.be/WRkYP7wnD40?t=175)

### Комбинирование интерполяций

```javascript
move = linear(time, tStart1, tEnd1, 0, x) - linear(time, tStart2, tEnd2, 0, x);
```

## Организация и оптимизация экспрешенов

- К экспрешенам удобнее всего добавлять слайдеры
- Переменные помогут с организацией кода
- Зацикленные экспрешенами анимации будут все-равно дополнительно просчитываться After Effects на протяжении всего таймлайна, что утяжеляет обработку кадров. Использование % помогает сделать зацикливание лучше, ае не будет перепросчитывать все кадры, а только основной цикл, все повторения будут просчитаны сразу же.
