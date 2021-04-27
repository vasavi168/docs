# Creating Message Templates

Your Message Templates will be reviewed to ensure they do not violate policies. Once approved, your business will have its own name where the Message Templates will live.

When creating a Message Temaple, you must have the following:

1. Message Template name
2. Translated Message Template in the correct format

### Examples

Creating a welcome message where the Message Template name is welcome and the message is

```
"Welcome {#var1#}. We look forward to serving you."
```

Creating an order confirmation message where the Message Template name is `order_confirmation` and the message is

```
"Your order {#var1#} for a total of {#var2#} is confirmed. The expected delivery is {#var3#}."
```

### Content Template Validations

- Two or more spaces are not supposed to use between 2 words, before word or afterword.
- All special characters (found on keyboard) are allowed, except < and > symbols
- Variable format is {#var#} which is case sensitive
- Or variable can be inserted by clicking the radio button (insert variable) above text box
- Trans/Service category messages should have variable mandatorily
- Promo category can have complete fixed content or with variable part
- There is no limitation in no.of variable per message
- Values like amount, date, a/c no, merchant names, OTP, codes, URL, customer names, card type, etc. needs to be - replaced with variables.

## Transactional

Any message which contains OTP and requires to complete a banking transaction initiated by bank customer will only be considered as transactional. This is applicable to all banks (national/scheduled/private/govt and even MNC's).

- OTP message required for completing a net-banking transaction.
- OTP message required for completing credit/debit card transactions at a merchant location.

## Service Implicit

Any message arising out of customers actions or his existing relationship with the enterprise, that is not promotional will be considered as Service-Implicit message.

- Confirmation messages of a Net-banking and credit/debit card transactions.
- Product purchase confirmation, delivery status, etc. from e-comm websites.
- Customer making payments through Payment Wallet over E-Commerce website / mobile app and an OTP is sent to complete - the transaction.
- OTP’s required for e-comm website, app login’s, social media apps, authentication/verification links, securities - trading, Demat account operations, KYC, e-wallet registration, etc.
- Messages from TSP/ISP.
- Periodic balance info, bill generation, bill dispatch, due date reminders, recharge confirmation (DTH, cable, - prepaid electricity recharge, etc.
- Delivery notifications, updates, and periodic upgrades.
- Messages from retail stores related to the bill, warranty.
- Messages from schools-attendance/transport alerts.
- Messages from hospitals/clinics/pharmacies/radiologists/pathologists about registration, appointment, discharge, - reports.
- Confirmatory messages from app-based services.
- Govt/DOT/TRAI mandated messages.
- Service updates from car workshops, repair shops, gadgets service centers.
- Directory services like Justdial, yellow pages.
- Day-end/month-end settlement alerts to securities/Demat account holders.

## Service Explicit

These are the messages which require explicit consent from the customer, that has been verified directly from the recipient in a robust and verifiable manner and recorded by the consent registrar. Any service message which doesn’t fall under the service-implicit category.

`Note: Additionally, the customer consent template needs to be linked to content templates in the service explicit category.`

Messages to the existing customers recommending or promoting their other products or services.

### Do’s for consent templates:

- Choose short name to a template which is relevant. This helps in choosing right consent template while creating - content templates in promotional or service explicit categories.
- Brand name should be relevant to details mentioned in scope of content.
- Scope of content should be relevant to mentioned brand & intent of the consent to be mentioned.
- If entity wants to provide opt-out information, that needs to be provided completely. E.g “To opt-out, send SMS as STOP to 1234567890”

### Don’ts for consent templates:

- Not to use generic names for templates like “template1; template2, etc.”
- Not to mention invalid or irrelevant names under brand. This will be treated as invalid template.
- Not to enter actual message sent to customer, no shot message like “consent; sms to customers; etc.”
- No variable to be used in scope of consent, as variable applicable to content templates only.
- Multiple consents not required by entity unless it is required by enterprise, like example mentioned explaining brand name field.

## Promotional

Any message with an intention to promote or sell a product, goods or service.Service content mixed with promotional content is also treated as promotional. These messages will be sent to customers after performing the preference and consent scrubbing function.

`Note: Additionally, customer consent template needs to be linked to content templates in service explicit category.`

### Do's for Content Template

- Use promotional category for communications intended to send from numerical sender id only.
- Transactional category to be used by banking enterprises only & for OTP messages during fund transfer; online - payment; merchant txn only.
- Service – explicit category needs to link consent template as well, without which the template gets rejected
- Choose a relevant/recognizable name for templates
- Use message type as "TEXT" for all general messages & "Unicode" for regional messages.
- Variable {#var#} insertion to be required against values like date; amount; a/c no; OTP; names; etc.
- Always use notepad or notepad ++ to create template, to avoid additional spaces and invalid characters
- Min fixed char required in templates is 6 char (applicable in pure OTP messages only)
- Linking of consent templates for content template categories "promotional" & "service – explicit" is optional (not mandatory)

### Don'ts for Content Template

- Not linking consent templates for content template categories "promotional" & "service – explicit". Same content - template against multiple headers.
- Header selection against irrelevant templates.
- Selecting "Transactional" category by non-banking enterprises.
- No or invalid variable format in templates.
- Using double spaces in templates (this can be pre-checked by verifying the template on notepad++ before template - submission).
- Templates with less than 6 char or variable insertion alone as a template.
- Do not use external fonts or characters other than those appear on keyboard.
