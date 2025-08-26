
# CardValidator

A Python library for credit card validation using the Luhn algorithm. Supports validation for **Visa**, **MasterCard**, **American Express**, **Discover**, and **RuPay** cards.

## Features

- ✅ **Luhn Algorithm Validation**: Industry-standard credit card validation.
- ✅ **Multiple Card Types**: Supports Visa, MasterCard, AmEx, Discover, and RuPay.
- ✅ **Input Flexibility**: Handles formatted input (spaces, hyphens).
- ✅ **Edge Case Handling**: Rejects invalid patterns like all-identical digits.
- ✅ **Zero Dependencies**: No external dependencies required.
- ✅ **Type Hints**: Full type annotation support.
- ✅ **Comprehensive Tests**: Well-tested with pytest.

## Installation

```
pip install cardvalidator
```

Or with [UV](https://github.com/astral-sh/uv):

```
uv add cardvalidator
```

## Quick Start

```
from cardvalidator import validate_card, is_valid_card, CardValidator

# Quick validation
result = validate_card("4111111111111111")
print(result)
# Output: {'card_number': '4111111111111111', 'valid': True, 'type': 'Visa', 'cleaned_number': '4111111111111111'}

# Simple boolean check
is_valid = is_valid_card("4111111111111111")
print(is_valid)  # Output: True

# Using the class directly
validator = CardValidator()
result = validator.validate("5105-1051-0510-5100")
print(result["type"])  # Output: MasterCard
```

## Supported Card Types

| Card Type           | Length        | Starts With              | Example             |
|---------------------|--------------|--------------------------|---------------------|
| **Visa**            | 13, 16, 19   | 4                        | 4111111111111111    |
| **MasterCard**      | 16           | 51-55                    | 5105105105105100    |
| **American Express**| 15           | 34, 37                   | 378282246310005     |
| **Discover**        | 16, 19       | 6011, 65, etc.           | 6011111111111117    |
| **RuPay**           | 16           | 60, 65, 81               | 6037997040000000*   |

*Test numbers for development use only

## API Reference

### `validate_card(card_number: str) -> dict`
Validates a card number and returns detailed information.

**Returns:**
```
{
    "card_number": "4111111111111111",
    "valid": True,
    "type": "Visa",
    "cleaned_number": "4111111111111111"
}
```

### `is_valid_card(card_number: str) -> bool`
Simple boolean validation.

### `CardValidator` Class
For advanced usage with custom validation logic.

## Development

### Setup

```
# Clone the repository
git clone https://github.com/yourusername/cardvalidator.git
cd cardvalidator

# Install with UV
uv sync

# Install in development mode
uv pip install -e .
```

### Running Tests

```
uv run pytest tests/ -v
```

### Building

```
uv build
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)  
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Implements the [Luhn Algorithm](https://en.wikipedia.org/wiki/Luhn_algorithm) for credit card validation.
- Supports Indian domestic payment network [RuPay](https://www.rupay.co.in/)
- Built with modern Python packaging standards using [UV](https://github.com/astral-sh/uv)

## Disclaimer

This library is for validation purposes only. Never store or transmit real credit card numbers in production applications without proper PCI DSS compliance.
