# Document eSigner — Bulk PDF Digital Signer for Windows

**Batch-sign hundreds of PDFs, or every page of 100+ page contracts, using your Class 3 DSC USB token — entirely offline.**

[![Website](https://img.shields.io/badge/website-documentesigner.in-00D4D4?style=flat-square)](https://www.documentesigner.in)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6?style=flat-square&logo=windows)](https://www.documentesigner.in)
[![License](https://img.shields.io/badge/license-Proprietary-lightgrey?style=flat-square)](#license)

[**Download the latest .exe →**](../../releases/latest) &nbsp;|&nbsp; [Visit documentesigner.in →](https://www.documentesigner.in)

---

## What is Document eSigner?

Document eSigner is a Windows desktop application built for Chartered Accountants, Company Secretaries, and businesses in India who need to apply digital signatures to PDFs **at scale**, using a hardware DSC (Digital Signature Certificate) token — without uploading a single file to the cloud.

Most PDF signing tools handle one file, one page, at a time. Document eSigner is built around two things they don't do well:

- **Bulk Files** — batch-sign hundreds of separate PDFs in a single run (Form 16s, TDS certificates, offer letters, vendor POs).
- **Bulk Pages** — automatically stamp every page of a single large document (100+ page tax audits, ledgers, board resolutions, tender papers) in one pass, instead of clicking through page by page.

## Why offline matters for DSC signing

Your DSC token's private key is meant to never leave the hardware token itself. Document eSigner's signing engine runs **100% locally**:

- PDF rendering and cryptographic signing happen on your machine, using direct [PKCS#11](https://en.wikipedia.org/wiki/PKCS_11) bindings to your token.
- Files, signatures, and key material are never uploaded anywhere.
- The only network calls the app makes are for account login and subscription/license checks — never for the documents themselves.

## Supported DSC USB tokens

Document eSigner talks directly to these tokens over PKCS#11:

| Token | Vendor |
|---|---|
| ProxKey | Watchdata (Pantagon) |
| ePass2003 | ePass |
| mToken | Trustkey / Various |
| mToken CryptoID | Trustkey |
| Watchdata | Watchdata |
| TrustKey | TrustKey Solutions |

If your Class 3 DSC token isn't listed, open an [issue](../../issues) and let us know the model — we're actively expanding driver support.

## Key features

- ✅ **Class 3 DSC compatible** — works with any CCA India–approved Class 3 certificate on a supported token
- ✅ **Bulk Files & Bulk Pages** signing modes
- ✅ **Pixel-precise stamp placement** — click-to-place or exact X/Y coordinates, per-page or custom page ranges
- ✅ **LTV (Long-Term Validation) & RFC 3161 timestamping** — signatures stay verifiable in Adobe Reader for years
- ✅ **Multi-certificate support** — switch between certificates on the same token
- ✅ **1-day free trial**, instant in-app account creation — no separate web signup required
- ✅ **UPI QR payments** (GPay / PhonePe / Paytm) for subscription renewal, directly in the app

## Who it's for

- **Chartered Accountants & Tax Practitioners** — Form 16, TDS certificates, GST e-invoices, tax audit reports requiring Class 3 DSC signing at volume
- **Company Secretaries & Legal Teams** — MCA21/ROC filings, board resolutions, 50–100+ page contracts
- **HR & Operations** — bulk offer letters, onboarding contracts, NDAs
- **Accounts Payable / Billing** — vendor POs, delivery challans, invoicing batches

## Installation

1. Go to the [Releases](../../releases) page and download the latest `.exe` installer.
2. Run the installer. Windows SmartScreen may show a warning since this is a new independent-developer app — click **"More info" → "Run anyway"** to proceed. This is normal and does not indicate the file is unsafe.
3. Launch the app, create an account in a few seconds, and your **1-day free trial** starts automatically.
4. Insert your Class 3 DSC USB token and start signing.

Full setup walkthrough: [documentesigner.in](https://www.documentesigner.in)

## Verifying your download

Every release includes a SHA-256 checksum. After downloading, verify it in PowerShell:

```powershell
Get-FileHash .\DocumentESigner-Setup.exe -Algorithm SHA256
```

Compare the output against the checksum listed on the corresponding [release page](../../releases).

## Tech stack

| Component | Technology |
|---|---|
| Desktop UI | WPF (.NET 8, Windows 10/11) + WPF-UI (Fluent theming) |
| PDF manipulation | PDFsharp |
| PDF preview / rasterization | PdfiumViewer.Core (PDFium) |
| Cryptography / CMS signing | BouncyCastle.Cryptography |
| Hardware token access | Pkcs11Interop (native PKCS#11 bindings) |
| Device fingerprinting | System.Management (WMI) |
| QR / image processing | OpenCvSharp4 + SkiaSharp |
| Installer & auto-update | Velopack |
| Licensing backend | FastAPI + MongoDB (closed-source) |

This repository hosts release binaries and documentation only. The application source is closed-source; releases are distributed here via GitHub Releases to avoid bandwidth limits on the main site.

## FAQ

**Does this upload my PDFs or DSC token to the cloud?**
No. All rendering and signing happen locally. The app only phones home to check your account/subscription status.

**Can it sign every page of a large PDF automatically?**
Yes — the Bulk Pages mode stamps every page of documents running to 100+ pages in a single pass, or a custom page range if you only need some pages signed.

**Which Windows versions are supported?**
Windows 10 and Windows 11 (64-bit).

**Is there a free trial?**
Yes, a 1-day full-access trial activates automatically when you create an account in the app.

## Support

- 🌐 Website: [documentesigner.in](https://www.documentesigner.in)
- ✉️ Contact: [documentesigner.in/contact](https://www.documentesigner.in/contact)
- 🐛 Bug reports & driver requests: [open an issue](../../issues)

## License

Document eSigner is closed-source, proprietary software. This repository is provided solely as a distribution and documentation hub for release binaries. See the [Terms & Conditions](https://www.documentesigner.in/terms) for usage terms.

---

<sub>Document eSigner is not affiliated with the Controller of Certifying Authorities (CCA) or the Government of India. "Class 3 DSC", "IT Act 2000", and related terms refer to the applicable Indian regulatory framework for digital signatures.</sub>
