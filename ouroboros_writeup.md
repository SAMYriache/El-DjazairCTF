# The Ouroboros Cipher - CTF Write-up

## Challenge Description
**Points:** 727  
**Category:** Crypto  
**Flag Format:** `El-DjazairCTF{...}`

> Beneath the Casbah's moonless vault, a bronze ouroboros—its scales etched with twin sigils, DJAZAIR in gold and ALGERIA in onyx—hungrily devours its tail. Each coil conceals one of three lost rites, penned in an arcane script older than the city itself. Only those who perceive the serpent's silent rhythm may one day hear the cabal's forgotten chant.

**Given Flag:** `El-DjazairCTF{OOPTUSAZUOBM}`

## Hints Analysis

**Hint 1:** *"The serpent starts at its tail, and nothing shines in a moonless sky."*
- "serpent starts at its tail" → Read from the end (reverse the text)
- "nothing shines in a moonless sky" → The key is **"moonless"**

**Hint 2:** *"Eight dark phases steer the cipher—turn them over the text once you've read it in the mirror."*
- "read it in the mirror" → Reverse/invert the text
- "turn them over" → Apply the cipher transformation

## Solution Approach

1. **Identify the cipher type:** Vigenère cipher based on the key hint
2. **Extract the encrypted part:** `OOPTUSAZUOBM`
3. **Apply transformations:**
   - Reverse the text: `MBOUZASUTPOO`
   - Use Vigenère decryption with key "MOONLESS"

## Implementation

```python
def vigenere_decode(ciphertext, key):
    result = ""
    key = key.upper()
    key_index = 0
    
    for char in ciphertext:
        if char.isalpha():
            shift = ord(key[key_index % len(key)]) - ord('A')
            decoded_char = chr((ord(char) - ord('A') - shift) % 26 + ord('A'))
            result += decoded_char
            key_index += 1
        else:
            result += char
    
    return result

# Solve
encrypted = "OOPTUSAZUOBM"
key = "MOONLESS"

# Step 1: Reverse the text
reversed_text = encrypted[::-1]  # "MBOUZASUTPOO"

# Step 2: Apply Vigenère decryption
decoded = vigenere_decode(reversed_text, key)

print(f"El-Djazair{{{decoded}}}")
```

## Step-by-step Decryption

| Position | Reversed Char | Key Char | Shift | Decoded Char |
|----------|---------------|----------|-------|--------------|
| 0        | M             | M        | 12    | A            |
| 1        | B             | O        | 14    | N            |
| 2        | O             | O        | 14    | A            |
| 3        | U             | N        | 13    | H            |
| 4        | Z             | L        | 11    | O            |
| 5        | A             | E        | 4     | W            |
| 6        | S             | S        | 18    | A            |
| 7        | U             | S        | 18    | C            |
| 8        | T             | M        | 12    | H            |
| 9        | P             | O        | 14    | B            |
| 10       | O             | O        | 14    | A            |
| 11       | O             | N        | 13    | B            |

## Final Flag
`El-DjazairCTF{ANAHOWACHBAB}`
`El-DjazairCTF{anahowachbab}`

## Key Takeaways
- The Ouroboros symbol (serpent eating its tail) was a strong hint for text reversal
- "Moonless" in the story description was the Vigenère key
- Combined cryptographic operations: reversal + Vigenère decryption
- Careful analysis of flavor text often contains crucial hints in CTF challenges
