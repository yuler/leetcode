# Unique Email Addresses

```JavaScript
/**
 * @param {string[]} emails
 * @return {number}
 */
var numUniqueEmails = function(emails) {
  emails = emails.map(email => {
    const index = email.indexOf('@')
    return email.slice(0, index).replace(/\./g, '').split('+')[0] + email.slice(index)
  })
  return new Set(emails).size
};
```