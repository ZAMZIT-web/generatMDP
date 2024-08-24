document.getElementById('generate').addEventListener('click', () => {
  const length = document.getElementById('length').value;
  const includeUppercase = document.getElementById('uppercase').checked;
  const includeNumbers = document.getElementById('numbers').checked;
  const includeSymbols = document.getElementById('symbols').checked;

  const password = generatePassword(length, includeUppercase, includeNumbers, includeSymbols);
  document.getElementById('password').value = password;
});

document.getElementById('copy').addEventListener('click', () => {
  const passwordField = document.getElementById('password');
  passwordField.select();
  document.execCommand('copy');
  alert('Password copied to clipboard!');
});

function generatePassword(length, uppercase, numbers, symbols) {
  const lowercaseChars = 'abcdefghijklmnopqrstuvwxyz';
  const uppercaseChars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  const numberChars = '0123456789';
  const symbolChars = '!@#$%^&*()_+[]{}|;:,.<>?';

  let charPool = lowercaseChars;
  if (uppercase) charPool += uppercaseChars;
  if (numbers) charPool += numberChars;
  if (symbols) charPool += symbolChars;

  let password = '';
  for (let i = 0; i < length; i++) {
    password += charPool.charAt(Math.floor(Math.random() * charPool.length));
  }
  return password;
}
