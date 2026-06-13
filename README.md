# 8086 Assembly Single-Digit Multiplication

A basic 8086 Assembly Language program written in MASM/TASM syntax that demonstrates how to perform arithmetic multiplication on user-inputted numbers using the `MUL` instruction and DOS interrupts (`INT 21H`).

## 🚀 Project Overview

This program captures two separate single-digit number inputs from the user, converts them from ASCII to actual numeric values, performs a multiplication operation, and then shifts the result back into ASCII format so it can be displayed as a readable number on the screen.

## 🛠️ How It Works & Logic

Assembly-te gun korar niom jog ba biyoger cheye thoda alada, karon `MUL` instruction ti nirdishtovabe `AL` register-er shathe kaj kore:

1. **First Input & Conversion:** Takes the first character (`AH = 1`). The ASCII value goes to `AL`. The program subtracts $48$ (`SUB AL, 48`) to get the **actual numeric value** and stores it in `BL`.
2. **Second Input & Conversion:** Takes the second character, converts it to a numeric value by subtracting $48$, and stores it in `CL`.
3. **The Multiplication (`MUL CL`):** * `MUL CL` instruction-ti implicit-babe (auto) `AL` register-er shathe `CL`-ke gun kore। 
   * Tai gun korar thik age, program-ti `MOV AL, BL` kore prothom shongkha-ti `AL`-e niye ashe।
   * Gunfol-ti (Result) automatic-babe `AX` register-e (choto shongkhar khetre `AL`-e) store hoy।
4. **ASCII Re-adjustment (`ADD AL, 48`):** Gunfol-ti screen-e dekhate hole take abar ASCII-te convert korte hoy। Tai `AL`-er shathe $48$ jog kora hoyeche।
5. **Output & Exit:** `AL`-er value-ti `DL`-e niye print kora hoy ebong program-ti safely sesh hoy (`AH = 4CH`)।
