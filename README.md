# Quantum Random Number Generator (QRNG)

🌟 **World's First Real Quantum Random Number Generator Implementation** 🌟

This implementation generates true random numbers using quantum mechanical principles, leveraging the fundamental randomness of quantum measurements through IBM's quantum computers.

## Overview

This quantum random number generator (QRNG) uses quantum superposition and measurement to produce truly random numbers. Unlike classical pseudo-random number generators that rely on deterministic algorithms, this implementation harnesses quantum mechanical properties to generate genuine randomness.

## How It Works

The generator works through the following steps:

1. **Quantum Circuit Creation**: Creates a quantum circuit with enough qubits to represent the desired number range
2. **Superposition**: Applies Hadamard gates to put all qubits in superposition
3. **Measurement**: Measures the quantum states to collapse the superposition
4. **Conversion**: Transforms the binary measurement results into decimal numbers

## Key Features

- Uses real quantum hardware when available
- Falls back to quantum simulator when necessary
- Configurable maximum value range
- Adjustable number of shots (measurements)
- Handles edge cases and ensures valid output

## Usage

```python
# Generate a random number between 0 and 100
random_num = generate_random_number(max_value=100)

# Generate multiple random numbers with multiple shots
random_nums = generate_random_number(max_value=100, shots=10)
```

## Dependencies

- Qiskit
- IBM Quantum Runtime Service
- Math (Python standard library)

## Code Example

```python
def generate_random_number(max_value=100, shots=1):
    """Generate a single random number between 0 and max_value."""
    # Calculate number of bits needed to represent max_value
    n_bits = math.ceil(math.log2(max_value + 1))
    
    # Create circuit
    qc = QuantumCircuit(n_bits, n_bits)
    
    # Apply Hadamard gates to create superposition on all qubits
    for i in range(n_bits):
        qc.h(i)
    
    # Measure all qubits
    qc.measure_all()
    
    # ... (See full implementation above)
```

## Technical Details

### Quantum Properties Used

- **Superposition**: Created using Hadamard gates
- **Quantum Measurement**: Provides true randomness through wave function collapse
- **Multi-qubit States**: Allows generation of numbers in any range

### Implementation Notes

- The number of qubits is calculated based on the maximum desired value
- Invalid measurements (numbers above max_value) are filtered out
- Recursive retry if no valid numbers are generated
- Supports both simulator and real quantum hardware execution

## Real Quantum Hardware Support

When `isSimulator` is set to `False`, the implementation:
1. Connects to IBM Quantum services
2. Finds the least busy available quantum computer
3. Executes the circuit on real quantum hardware
4. Processes results from actual quantum measurements

## Error Handling

- Automatically retries if no valid numbers are generated
- Handles quantum hardware connection issues
- Validates output range

## Limitations

- Maximum value must be positive
- Execution time depends on quantum hardware availability
- May require queue time on real quantum computers

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:
- Performance improvements
- Additional features
- Documentation updates
- Bug fixes

## License

MIT


---
Created with 💫 quantum randomness
