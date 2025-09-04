# rakshitha_pipingrock
This task is to assess your ability to quickly build and execute automation tests in a userfriendly manner.


# DemoQA Automation Testing Framework

A comprehensive automation testing framework for the DemoQA website using JavaScript and Playwright. This framework covers all major UI elements including checkboxes, web tables, dynamic properties, file uploads, and date pickers.

## Test Results Overview

Based on the test execution shown in the images:
- ✅ **20 Total Tests** executed
- ✅ **12 Tests Passed** 
- ❌ **2 Tests Failed**
- ⚠️ **6 Tests Flaky** (intermittent issues)
- **Total Execution Time**: 13.2 minutes

## Framework Setup Instructions

### Prerequisites
- **Node.js** (version 14 or higher) - [Download from nodejs.org](https://nodejs.org/)
- **VS Code** - [Download from code.visualstudio.com](https://code.visualstudio.com/)
- **Internet Connection** - Required for downloading browser binaries

### Step-by-Step Setup

1. **Create Project Directory**
   ```bash
   mkdir demoqa-automation
   cd demoqa-automation
   ```

2. **Open in VS Code**
   ```bash
   code .
   ```

3. **Initialize Node.js Project**
   ```bash
   npm init -y
   ```

4. **Install Playwright Testing Framework**
   ```bash
   npm install --save-dev @playwright/test
   ```

5. **Install Browser Binaries**
   ```bash
   npx playwright install
   ```

6. **Create Project Structure**
   ```
   demoqa-automation/
   ├── tests/
   │   ├── checkbox.test.js
   │   ├── webTables.test.js
   │   ├── dynamicProperties.test.js
   │   ├── fileUpload.test.js
   │   └── datePicker.test.js
   ├── playwright.config.js
   ├── package.json
   └── README.md
   ```

7. **Copy Test Files** - Use the provided test files from the previous artifacts

## Steps to Execute Tests

### Option 1: Run All Tests (Recommended)
```bash
npm run test:headed
```

### Option 2: Run with Playwright UI (Best for Debugging)
```bash
npm run test:ui
```

### Option 3: Run Specific Test Categories
```bash
# Run only checkbox tests
npx playwright test checkbox.test.js --headed

# Run only web tables tests
npx playwright test webTables.test.js --headed

# Run only dynamic properties tests
npx playwright test dynamicProperties.test.js --headed

# Run only file upload tests
npx playwright test fileUpload.test.js --headed

# Run only date picker tests
npx playwright test datePicker.test.js --headed
```

### Option 4: Run Tests Headless (Background)
```bash
npm test
```

### Option 5: Debug Specific Failed Test
```bash
npx playwright test --grep "should validate button color change" --debug
```

## Test Categories Covered

### 1. Checkbox Automation Tests
- ✅ Navigate and check classified checkbox
- ⚠️ Expand and collapse tree nodes (flaky due to dynamic loading)
- ✅ Handle checkbox toggle functionality

### 2. Web Tables Automation Tests
- ✅ Add new row to web table
- ✅ Delete row from web table
- ✅ Extract and validate table data
- ❌ Edit existing row (element selector needs refinement)
- ✅ Search for specific records

### 3. Dynamic Properties Automation Tests
- ✅ Validate enable after button functionality
- ✅ Test all dynamic properties together
- ❌ Validate button color change after delay (timing issue)
- ⚠️ Validate visible after button functionality (intermittent)

### 4. File Upload Automation Tests
- ⚠️ Upload file successfully (path resolution issue)
- ✅ Handle download functionality
- ✅ Validate file input properties

### 5. Date Picker Automation Tests
- ✅ Select date using simple date picker
- ✅ Navigate between months in date picker
- ✅ Handle weekend dates in date picker
- ⚠️ Select date and time using date time picker (complex selector)
- ⚠️ Select current date (dynamic date handling)

## Key Features

- **Cross-Browser Testing**: Runs on Chromium, Firefox, and WebKit
- **Visual Testing**: Browser opens during test execution
- **Automatic Screenshots**: Captures screenshots on test failures
- **Video Recording**: Records videos for failed tests
- **Detailed Reporting**: HTML reports with test results
- **Parallel Execution**: Tests run in parallel for faster execution

## Troubleshooting Common Issues

### Flaky Tests (Yellow Warning Icons)
These tests pass sometimes but fail intermittently due to:
- **Network delays** when loading dynamic content
- **Timing issues** with animations and transitions
- **Element visibility** changes during page load

**Solutions**:
- Increase timeout values in playwright.config.js
- Add explicit waits for dynamic elements
- Use more robust selectors

### Failed Tests (Red X Icons)
Common causes and solutions:

1. **Element Not Found**
   ```bash
   # Debug with UI mode to inspect elements
   npx playwright test --ui
   ```

2. **Timeout Issues**
   - Increase timeout in playwright.config.js
   - Check internet connection
   - Verify DemoQA website is accessible

3. **Selector Issues**
   - Use Playwright's code generator to get accurate selectors:
   ```bash
   npx playwright codegen https://demoqa.com
   ```

## Assumptions Made

### Technical Assumptions
1. **Node.js Environment**: Assumed Node.js 14+ is available or can be installed
2. **Browser Compatibility**: Tests are optimized for Chromium-based browsers
3. **Internet Connectivity**: Stable internet connection for accessing DemoQA website
4. **VS Code Usage**: Instructions tailored for VS Code development environment

### Test Environment Assumptions
1. **DemoQA Website Availability**: Assumed the website is consistently accessible
2. **Dynamic Content Loading**: Some elements have dynamic loading times (2-5 seconds)
3. **File System Access**: Local file system access for file upload tests
4. **Date Picker Behavior**: Date pickers use React components with specific selectors

### Test Data Assumptions
1. **Temporary Test Data**: All test data is temporary and doesn't persist
2. **Unique Identifiers**: Using timestamp-based or random data to avoid conflicts
3. **File Types**: Upload tests assume support for common file types (.txt, .pdf, .jpg)
4. **Browser Permissions**: Assumed default browser settings allow file uploads

### Performance Assumptions
1. **Test Duration**: Individual tests should complete within 30 seconds
2. **Network Latency**: Accounted for up to 5-second delays in element loading
3. **Parallel Execution**: Assumed system can handle multiple browser instances

## Maintenance Notes

### Regular Updates Needed
- **Browser Versions**: Update Playwright browsers monthly
  ```bash
  npx playwright install
  ```
- **Dependencies**: Update npm packages quarterly
  ```bash
  npm update
  ```

### Monitoring Test Health
- **Flaky Test Threshold**: If flakiness > 20%, investigate root cause
- **Failed Test Investigation**: Review screenshots and videos in `test-results/` folder
- **Performance Monitoring**: Monitor test execution times for degradation

## Support and Extension

### Adding New Tests
1. Create new test file in `tests/` folder
2. Follow existing naming convention: `feature.test.js`
3. Use provided helper functions for consistency

### Custom Configuration
- Modify `playwright.config.js` for different browsers or settings
- Adjust timeouts based on your network conditions
- Enable/disable video recording based on storage needs

### Reporting
- HTML reports generated automatically in `playwright-report/`
- View detailed test results: `npx playwright show-report`
- CI/CD integration possible with minor configuration changes

---

**Framework Version**: 1.0.0  
**Last Updated**: September 2025  
**Compatibility**: Node.js 14+, Playwright 1.40+
