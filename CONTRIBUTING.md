# Contributing

Contributions to this project are [released](https://help.github.com/articles/github-terms-of-service/#6-contributions-under-repository-license) to the public under the [project's open source license](LICENSE).

Everyone is welcome to contribute to this project. Contributing doesn't just mean submitting pull requests—there are many different ways for you to get involved, including answering questions, reporting issues, improving documentation, or suggesting new features.

## How to Contribute

### Reporting Issues

If you find a bug or have a feature request:
1. Check if the issue already exists in the [GitHub Issues](https://github.com/orassayag/nodejs-layered-architecture/issues)
2. If not, create a new issue with:
   - Clear title and description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Error messages or logs (if applicable)
   - Your environment details (OS, Node version, MongoDB version)

### Submitting Pull Requests

1. Fork the repository
2. Create a new branch for your feature/fix:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Make your changes following the code style guidelines below
4. Test your changes thoroughly
5. Commit with clear, descriptive messages
6. Push to your fork and submit a pull request

### Code Style Guidelines

This project uses:
- **JavaScript** (Node.js)
- **ESLint** with Airbnb configuration for code quality
- **Prettier** for code formatting
- **Husky** and **lint-staged** for pre-commit hooks

Before submitting:
```bash
# Install dependencies
npm install

# Check for linting errors
npm run lint

# Run tests
npm test

# Run unit tests only
npm run test:unit

# Run component tests only
npm run test:component
```

### Coding Standards

1. **Layered Architecture**: Follow the existing pattern:
   - Controllers: HTTP handling only
   - Services: Business logic
   - Repositories: Data access
   - Middlewares: Cross-cutting concerns

2. **Error handling**: Use try-catch with proper error middleware

3. **Dependency injection**: Pass dependencies through function parameters

4. **Testing**: 
   - Write unit tests for services and controllers
   - Write component tests for integration scenarios
   - Use Mocha for testing framework
   - Use Supertest for HTTP testing

5. **Naming conventions**: Use clear, descriptive names following JavaScript conventions

6. **Validation**: Use Joi for input validation

### Adding New Features

When adding new features:
1. Follow the layered architecture pattern
2. Add appropriate routes in `src/routes/`
3. Implement controllers in `src/controllers/`
4. Add business logic in `src/services/`
5. Implement data access in `src/repositories/`
6. Add validation middleware if needed
7. Write comprehensive tests
8. Update documentation

### Testing Guidelines

- Test files should mirror the source structure
- Unit tests in `test/unit/`
- Component/integration tests in `test/component/`
- Mock external dependencies appropriately
- Aim for good test coverage

## Questions or Need Help?

Please feel free to contact me with any question, comment, pull-request, issue, or any other thing you have in mind.

* Or Assayag <orassayag@gmail.com>
* GitHub: https://github.com/orassayag
* StackOverflow: https://stackoverflow.com/users/4442606/or-assayag?tab=profile
* LinkedIn: https://linkedin.com/in/orassayag

Thank you for contributing! 🙏
