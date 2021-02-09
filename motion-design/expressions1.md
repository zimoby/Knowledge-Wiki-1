# Expressions Part 1

По мере увеличения опыта работы в любом софте, мы начинаем сталкиваться с их ограничениями, которые не решаются простыми базовыми манипуляциями с интерфейсом. Это ограничения самого дизайна софта. В большинстве случае в редакторах компьютерной графики есть встроенный язык программирования расширяющий возможности. Экспрешены одни из таких решений.

Экспрешены нужны для:
- Автоматизации анимации
- Рандоматизации значений
- Создание сложных взаимосвязей для создания сетапов и ригов 

## Links

- [Top 3 After Effects Expressions to Simplify Your Workflow](https://blog.motiondesign.school/top-3-after-effects-expressions)
- [4 Advanced After Effects Expressions Made Easy](https://blog.motiondesign.school/4-advanced-after-effects-expressions)

## Randomizers

### Wiggle

{% tabs %} {% tab title="Wiggle Short" %}
```text
wiggle(1, 20);
```
{% endtab %}

{% tab title="Wiggle Long" %}
```text
freq = 1
amp = 20;
wiggle(freq, amp);
```
{% endtab %}

{% tab title="Wiggle Randomize" %}
```text
freq = 1
amp = 20;
seed = 1;
seedRandom(seed, false);
wiggle(freq, amp);
```
{% endtab %} {% endtabs %}

#### Дополнительный материал
