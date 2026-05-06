# License Information

## Your License
- **License Key:** `312E-B740-910B-BAF9`
- **Product:** telegram-mini-faucet-secure-crypto-rewards-faucet--f4a84c
- **Version:** 1.0.0

## Important Files
- `license.json` - Contains your license key and validation URL
- `LICENSE_KEY.txt` - Plain text license key for reference

## How License Validation Works

Your application validates the license at runtime by calling our API. The `license.json` file contains the minimum information needed:

```json
{
  "license_key": "YOUR-LICENSE-KEY",
  "product_id": "product-id",
  "validation_url": "https://license-management-production-87f2.up.railway.app/api/licenses/validate",
  "info_url": "https://license-management-production-87f2.up.railway.app/api/licenses/info"
}
```

### Basic Validation

```javascript
const license = require('./license.json');

async function validateLicense(domain) {
  const response = await fetch(license.validation_url, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      licenseKey: license.license_key,
      domain: domain,
      productId: license.product_id
    })
  });
  
  const result = await response.json();
  return result.valid;
}
```

### Getting Full License Details (Optional)

If your application needs additional license information (expiry date, license type, etc.), fetch it from the info endpoint:

```javascript
async function getLicenseInfo() {
  const response = await fetch(`${license.info_url}?licenseKey=${license.license_key}`);
  return await response.json();
}
```

## Support

For license issues or technical support, please contact the vendor.

---
*This file was automatically generated during download.*
