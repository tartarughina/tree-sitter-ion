# tree-sitter-ion

A [Tree-sitter](https://tree-sitter.github.io/tree-sitter/) grammar for [Amazon Ion](https://amzn.github.io/ion-docs/).

## About Amazon Ion

Amazon Ion is a richly-typed, self-describing, hierarchical data serialization format offering interchangeable binary and text representations. Ion was built to address rapid development, decoupling, and efficiency challenges faced every day while engineering large-scale, service-oriented architectures.

## Features

This grammar supports all Ion data types and features:

- **Scalar Types**: null, bool, int, float, decimal, timestamp, string, symbol, blob, clob
- **Container Types**: list, sexp (S-expressions), struct
- **Annotations**: Type annotations using `::` syntax
- **Comments**: Both line comments (`//`) and block comments (`/* */`)
- **All Ion Literals**: Including hex integers, binary integers, scientific notation, etc.

## Installation

### For Tree-sitter CLI

```bash
npm install tree-sitter-ion
```

### For Neovim with nvim-treesitter

Add to your Neovim configuration:

```lua
require'nvim-treesitter.configs'.setup {
  ensure_installed = { "ion" },
  -- ... other config
}
```

## Usage

### With Tree-sitter CLI

```bash
# Parse an Ion file
tree-sitter parse example.ion

# Test the grammar
tree-sitter test
```

### Example Ion Code

```ion
// Ion supports rich data types
{
  name: "John Doe",
  age: 30,
  active: true,
  balance: 1234.56d,
  created: 2023-01-01T00:00:00Z,
  tags: ["customer", "premium"],
  metadata: {
    source: 'web',
    score: null.int
  }
}

// Annotations provide type information
person::{
  name: "Jane",
  contact: email::"jane@example.com"
}
```

## Grammar Development

### Building

```bash
# Generate the parser
tree-sitter generate

# Run tests
tree-sitter test

# Test with a specific file
tree-sitter parse path/to/file.ion
```

### Testing

The grammar includes comprehensive tests covering all Ion data types and edge cases. Tests are located in `test/corpus/`.

## Resources

- [Ion Specification](https://amzn.github.io/ion-docs/docs/spec.html)
- [Ion Grammar Reference](https://amazon-ion.github.io/ion-docs/grammar/IonText.g4.txt)
- [Tree-sitter Documentation](https://tree-sitter.github.io/tree-sitter/)

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
