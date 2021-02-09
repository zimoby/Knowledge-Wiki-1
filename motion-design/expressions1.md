# Expressions Part 1

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
