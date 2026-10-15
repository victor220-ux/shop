SUSU CLOTHING STORE — PACKAGE GUIDE

storefront files: index.html, style.css, app.js
admin files: admin.html, admin.css, admin.js

The storefront reads the existing Supabase store-catalog Edge Function and places orders through checkout-cod. It displays real compare-at price reductions and savings, an estimated promo-code discount when the active promo is available in the public catalogue, and a delivery estimate only when the entered city matches a published active delivery zone. The server remains authoritative for final checkout calculations. The public catalogue now includes promotion minimum-subtotal values and per-variant stock quantities so the UI can give better estimates.

ADMIN
Open admin.html after deploying alongside the storefront. Sign in using an existing Supabase Auth account whose public.profiles.role is already 'admin'. This interface does not grant admin roles and has no backdoor account creation. Supabase RLS is expected to enforce access on database operations.

The admin provides product create/edit/publish, image upload to the existing product-images bucket, category management, per-product variants, order review and status updates, promotion creation/toggling, and delivery-zone creation/toggling.

IMPORTANT CHECKS BEFORE PUBLIC LAUNCH
1. Confirm the production GitHub Pages origin is in the allowedOrigins set for both Edge Functions. The current functions allow https://victor220-ux.github.io.
2. Test with an authorised admin account and a non-admin account.
3. Verify the checkout SQL function's delivery-zone matching behavior and ensure zone city names match it exactly.
4. Configure at least one real active delivery zone before accepting live orders. A database guard now blocks order creation until at least one active delivery zone exists; checkout also rejects cities without a matching zone. Delivery fees and free-delivery thresholds are calculated server-side from the matching city.
5. Review promotions against SQL enforcement; client-side estimates are never authoritative.
6. Configure Supabase Auth leaked-password protection manually in dashboard.
7. Use real product photos and accurate product/stock data. Do not use generated placeholders as real merchandise images.
8. This package does not enable payments other than the existing cash-on-delivery flow.

No Student Insights or agency-site files are included in this ZIP.
