# How to Upload to PyPI (Global pip)

Your package has been built successfully! Here's how to upload it to PyPI so anyone can install it with `pip install air-gesture-command`.

## Files Created

Your distribution files are in the `dist/` directory:

- `air_gesture_command-0.1.1.tar.gz` - Source distribution
- `air_gesture_command-0.1.1-py3-none-any.whl` - Wheel distribution (preferred)

## Step 1: Create PyPI Account

1. Go to https://pypi.org/account/register/
2. Create a free account
3. Verify your email address

## Step 2: Create TestPyPI Account (Optional but Recommended)

Test your upload on TestPyPI first:

1. Go to https://test.pypi.org/account/register/
2. Create a free account
3. Verify your email address

## Step 3: Generate API Token

### For Production PyPI:

1. Log in to https://pypi.org
2. Click on your username → Account settings
3. Scroll to "API tokens" section
4. Click "Add API token"
5. Name it (e.g., "air-gesture-command-upload")
6. Set scope to "Entire account" or specific to your project
7. **Copy the token immediately** (you won't see it again)
   - Format: `pypi-...`

### For TestPyPI (if testing):

1. Log in to https://test.pypi.org
2. Follow same steps as above

## Step 4: Upload to TestPyPI (Optional Test)

First, test on TestPyPI:

```bash
/usr/local/bin/python3 -m twine upload --repository testpypi dist/*
```

When prompted:

- Username: `__token__`
- Password: Your TestPyPI token (paste it, including `pypi-` prefix)

To test installation from TestPyPI:

```bash
pip install --index-url https://test.pypi.org/simple/ air-gesture-command
```

## Step 5: Upload to Production PyPI

When you're ready to upload to the real PyPI:

```bash
/usr/local/bin/python3 -m twine upload dist/*
```

When prompted:

- Username: `__token__`
- Password: Your PyPI token (paste it, including `pypi-` prefix)

### Alternative: Use .pypirc File

To avoid entering credentials each time, create `~/.pypirc`:

```ini
[pypi]
username = __token__
password = pypi-YOUR_TOKEN_HERE

[testpypi]
username = __token__
password = pypi-YOUR_TESTPYPI_TOKEN_HERE
```

Then upload with:

```bash
/usr/local/bin/python3 -m twine upload dist/*
```

## Step 6: Verify Upload

After successful upload:

1. Visit https://pypi.org/project/air-gesture-command/
2. Check that your package appears correctly

## Step 7: Install Your Package Globally

Anyone can now install your package with:

```bash
pip install air-gesture-command
```

And run it with:

```bash
air-command
```

## Updating Your Package

When you make changes:

1. Update the version number in `pyproject.toml` (e.g., from `0.1.1` to `0.1.2`)
2. Clean old builds:
   ```bash
   rm -rf dist/ build/ *.egg-info
   ```
3. Rebuild:
   ```bash
   /usr/local/bin/python3 -m build
   ```
4. Upload new version:
   ```bash
   /usr/local/bin/python3 -m twine upload dist/*
   ```

## Important Notes

⚠️ **Package names are permanent** - You can't delete a package from PyPI, only "yank" versions
⚠️ **Version numbers are final** - Once uploaded, you can't re-upload the same version
⚠️ **Test first** - Always test on TestPyPI before uploading to production PyPI
✅ **Update version** - Increment version number for each upload

## Troubleshooting

### "File already exists"

- You're trying to upload a version that already exists
- Increment the version number in `pyproject.toml`

### "Invalid credentials"

- Make sure username is exactly `__token__` (with double underscores)
- Check your token is complete and correct
- Verify you're using the right token (PyPI vs TestPyPI)

### "Package name already taken"

- Choose a different package name in `pyproject.toml`
- Try variations like `air-gesture-commands` or `gesture-air-command`

## Security Best Practices

1. **Never commit tokens** to git
2. Add `.pypirc` to `.gitignore`
3. Use project-scoped tokens when possible
4. Rotate tokens periodically
5. Use different tokens for different projects

---

Good luck with your PyPI upload! 🚀
