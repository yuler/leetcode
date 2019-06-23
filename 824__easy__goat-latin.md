# Goat Latin

```JavaScript
/**
 * @param {string} S
 * @return {string}
 */
var toGoatLatin = function(S) {
  return S.split(' ')
    .map((word, index) => {
      if (/^[aeiou]/i.test(word[0])) {
        return word + 'ma' + 'a'.repeat(index + 1)
      }
      return word.slice(1) + word[0] + 'ma' + 'a'.repeat(index + 1)
    })
    .join(' ')
};
```