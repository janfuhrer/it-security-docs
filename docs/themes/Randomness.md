tags: #symmetric #Randomness 

# Randomness

links:  [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]

---

## Definition

Randomness refers to a phenomenon or process that is without pattern, order or predictability. In simple terms, it denotes a condition where every possible outcome or event has an equal chance of occurrence (uniform distribution).

## Requirements of Randomness

1. **Unpredictability**: A random sequence can't be reasonably predicted.
2. **Lack of Pattern**: There should be no discernible pattern or order in a random sequence.
3. **Balance**: In a large enough sample, each possible outcome should occur roughly with the same frequency.
4. **Independence**: The occurrence of one event should not affect the occurrence of another event.

## Sources of Randomness

Nature / Physics is the source we use for Randomness.

- Quantum Mechanics (Radioactive decay, quantum superpositions)
- Atmospheric Noise (Noise in radio & television signals)
- Biological Processes
- Dice and Lottery Draws (If they are fair)
- Latte Macchiato
- From Hardware sources (Keyboard timings, mouse movements, audio, temperature etc.)

## Askew events

Askew events refer to events that are slightly off from the norm, unpredictable, or irregular.

Hardware sources mentioned above are an example of askew events. Another example is CPU Jitter

## CPU Jitter

Jitter refers to the small, unpredictable variations in the timing of events, such as the execution of instructions by a CPU. These variations are caused by factors such as system interrupts, background processes, or fluctuations in system clock speed (and temperature). By measuring and analysing these timing variations, a CPU Jitter RNG can generate random numbers that are believed to be statistically random and suitable for cryptographic applications or other scenarios that require high-quality randomness.

The concept behind a CPU Jitter RNG is that the precise timing of CPU instructions is difficult to predict due to the dynamic nature of computer systems and the complexity of concurrent processes running on them. By leveraging these timing variations, the RNG can extract random bits and construct random numbers.

Sources on Jitter entropy:

- [Clearification and justification of jittering as entropy source](http://www.chronox.de/jent.html)
-  [Example implementation](https://github.com/smuellerDD/jitterentropy-library)

---
links:  [[103 AC1 TOC - Randomness|AC1 TOC - Randomness]] - [[themes/000 Index|Index]]