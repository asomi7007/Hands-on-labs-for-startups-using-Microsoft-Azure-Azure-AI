# Contributing to Hands-on Labs for Startups

Thank you for your interest in contributing to this Azure & Azure AI workshop! We welcome contributions from the community to help improve and expand these learning materials.

## 🎯 How You Can Contribute

There are many ways to contribute to this project:

- 🐛 **Report bugs or issues** with the labs
- 💡 **Suggest new features** or improvements
- 📝 **Improve documentation** and fix typos
- 🔧 **Submit code fixes** or enhancements
- 🌍 **Translate content** to other languages
- 📚 **Share your experience** and feedback

## 🚀 Getting Started

### 1. Fork and Clone

```bash
# Fork this repository on GitHub
# Then clone your fork
git clone https://github.com/YOUR_USERNAME/Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI.git
cd Hands-on-labs-for-startups-using-Microsoft-Azure-Azure-AI
```

### 2. Set Up Development Environment

```bash
# Create virtual environment
python -m venv .venv

# Activate virtual environment
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Start MkDocs dev server
mkdocs serve
```

Visit http://127.0.0.1:8000 to preview your changes.

### 3. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
# or
git checkout -b docs/your-documentation-update
```

## 📝 Contribution Guidelines

### Documentation Style Guide

#### Writing Style
- ✅ Use clear, concise language
- ✅ Write in Korean for Korean content
- ✅ Use active voice
- ✅ Include code examples where appropriate
- ✅ Add screenshots or diagrams for complex concepts
- ✅ Use emoji sparingly for visual clarity (📚 🚀 ✅ ⚠️)

#### Markdown Formatting
- Use `#` for main titles (H1)
- Use `##` for sections (H2)
- Use `###` for subsections (H3)
- Use code blocks with language specification:
  ```python
  # Python example
  print("Hello, Azure!")
  ```
- Use admonitions for important notes:
  ```markdown
  > 💡 **Tip**: Helpful information here
  > ⚠️ **Warning**: Important caution
  > ✅ **Success**: What to expect
  ```

#### Lab Document Structure

Each lab should follow this structure:

```
docs/labN/
├── index.md          # Overview and quick start
├── introduction.md   # Background and architecture
├── development.md    # Step-by-step implementation
├── deployment.md     # Deployment instructions
├── security.md       # Security considerations
├── resources.md      # Additional resources
├── conversation.md   # FAQ and troubleshooting
└── summary.md        # Completion checklist and next steps
```

### Code Style Guide

#### Python Code
- Follow [PEP 8](https://pep8.org/) style guide
- Use type hints where appropriate
- Add docstrings for functions and classes
- Keep functions small and focused
- Use meaningful variable names

```python
def calculate_total_cost(items: list[dict], tax_rate: float = 0.1) -> float:
    """
    Calculate total cost including tax.
    
    Args:
        items: List of items with 'price' key
        tax_rate: Tax rate as decimal (default 0.1 = 10%)
    
    Returns:
        Total cost including tax
    """
    subtotal = sum(item['price'] for item in items)
    return subtotal * (1 + tax_rate)
```

#### JavaScript/TypeScript Code
- Use modern ES6+ syntax
- Prefer `const` over `let`, avoid `var`
- Use arrow functions for callbacks
- Add JSDoc comments for functions

```typescript
/**
 * Fetch user data from API
 * @param userId - Unique user identifier
 * @returns Promise with user data
 */
async function fetchUserData(userId: string): Promise<User> {
    const response = await fetch(`/api/users/${userId}`);
    return response.json();
}
```

### Commit Message Guidelines

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```bash
feat(lab5): Add WebSocket connection manager example

docs(lab1): Update Azure credit application steps

fix(lab2): Correct WordPress chatbot integration code

chore: Update dependencies to latest versions
```

## 🔍 Testing Your Changes

### Test Documentation Locally

```bash
# Start development server
mkdocs serve

# Build static site
mkdocs build

# Check for broken links (if you have linkchecker installed)
linkchecker http://127.0.0.1:8000
```

### Test Code Changes

```bash
# Run Python tests (if applicable)
pytest

# Check code style
flake8 .
black --check .

# Type checking
mypy .
```

## 📬 Submitting Your Contribution

### Pull Request Process

1. **Update Documentation**: Ensure any new features are documented
2. **Test Thoroughly**: Verify your changes work as expected
3. **Update Changelog**: Add entry to CHANGELOG.md (if applicable)
4. **Commit Changes**: Use meaningful commit messages
5. **Push to Fork**: Push your branch to your GitHub fork
6. **Create Pull Request**: Open a PR with a clear description

### Pull Request Template

```markdown
## Description
Brief description of what this PR does

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Code refactoring

## Testing
- [ ] Tested locally
- [ ] Documentation builds without errors
- [ ] Code follows style guidelines

## Related Issues
Closes #(issue number)

## Screenshots (if applicable)
Add screenshots to help reviewers

## Additional Notes
Any other information that would be helpful
```

### Review Process

1. A maintainer will review your PR within 7 days
2. Address any feedback or requested changes
3. Once approved, your PR will be merged
4. You'll be added to the contributors list! 🎉

## 🐛 Reporting Issues

### Before Creating an Issue

- Check if the issue already exists
- Verify you're using the latest version
- Test with a fresh environment

### Issue Template

```markdown
**Lab/Section:** Lab 1 - Azure Credits

**Description:**
Clear description of the issue

**Steps to Reproduce:**
1. Go to '...'
2. Click on '...'
3. See error

**Expected Behavior:**
What should happen

**Actual Behavior:**
What actually happens

**Screenshots:**
If applicable

**Environment:**
- OS: [e.g., Windows 11, macOS 13]
- Browser: [e.g., Chrome 120]
- Python Version: [e.g., 3.11]
```

## 💬 Communication

### Where to Ask Questions

- **GitHub Discussions**: For general questions and discussions
- **GitHub Issues**: For bug reports and feature requests
- **Pull Request Comments**: For questions about specific changes

### Code of Conduct

Please note that this project follows the [Microsoft Open Source Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

## 📚 Additional Resources

### MkDocs & Material Theme
- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)
- [Markdown Guide](https://www.markdownguide.org/)

### Azure Documentation
- [Azure Docs](https://docs.microsoft.com/azure/)
- [Azure Architecture Center](https://learn.microsoft.com/azure/architecture/)

### Git & GitHub
- [GitHub Docs](https://docs.github.com/)
- [Pro Git Book](https://git-scm.com/book/en/v2)

## 🎖️ Recognition

Contributors will be recognized in:
- README.md contributors section
- GitHub contributors graph
- Release notes (for significant contributions)

## 📄 License

By contributing, you agree that your contributions will be licensed under the same [MIT License](LICENSE) that covers this project.

---

Thank you for contributing to make this workshop better for everyone! 🙌

If you have any questions about contributing, feel free to:
- Open a discussion on GitHub
- Reach out to the maintainers
- Check existing issues and PRs for examples

**Happy Contributing! 🚀**
