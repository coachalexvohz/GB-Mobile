
# Configuration Resend pour GB Mobile

## Étapes de Configuration

### 1. Configuration DNS (Obligatoire)

Vous devez configurer les enregistrements DNS suivants dans votre domaine `gbmobilemecanique.abacusai.app` :

**Enregistrements DKIM et SPF :**
```
Type: MX
Name: send.gbmobilemecanique
Content: feedback-smtp.us-east-1.amazonses.com
TTL: Auto
Priority: 10

Type: TXT
Name: send.gbmobilemecanique
Content: v=spf1 include:amazonses.com ~all
TTL: Auto

Type: TXT
Name: resend._domainkey.gbmobilemecanique
Content: p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDDpuhwRvituG4P2oMBSFue9rk9Z/JFCb1kNcc1t/zB6xL5+f3hO2PaKRNChj95GxEg0vIH805BBqeQ5wMsChgkSyGNEFWfrbiKVWkAveOfrNfAuaqbG0fcpT/SbWObyZtQ2RgrIo3eFIN+iBLd1/HTW+iK6hOspWNCDA6JkI+C2wIDAQAB
TTL: Auto

Type: TXT
Name: _dmarc
Content: v=DMARC1; p=none;
TTL: Auto
```

**⚠️ IMPORTANT :** Suivez le guide officiel d'Abacus.AI pour configurer ces DNS :
👉 **[Guide Configuration DNS](https://abacus.ai/help/howTo/chatllm/app_deployment_and_custom_domain_how_to)**

### 2. Configuration de l'API Key Resend

Une fois les DNS configurés, ajoutez votre clé API Resend dans le fichier `.env` :

```bash
# Dans .env
RESEND_API_KEY="your_actual_resend_api_key_here"
```

**Pour obtenir votre clé API :**
1. Connectez-vous à [resend.com](https://resend.com)
2. Allez dans "API Keys" 
3. Créez une nouvelle clé API
4. Copiez-la et remplacez `"your_resend_api_key_here"` dans `.env`

### 3. Test de la Configuration

Une fois configuré, testez les formulaires :

1. **Formulaire de Contact** : `/contact` (onglet "Contact Form")
2. **Formulaire de Réservation** : `/contact` (onglet "Booking Form") 
3. **Formulaire de Témoignage** : `/testimonials`

### 4. Fonctionnalités Email

L'intégration Resend inclut :

✅ **Formulaire de Contact**
- Emails avec design HTML professionnel
- Informations de contact formatées
- Réponse automatique possible

✅ **Formulaire de Réservation**
- Emails urgents pour les réservations
- Détails complets du service demandé  
- Informations du véhicule et localisation

✅ **Formulaire de Témoignage**
- Notifications des nouveaux témoignages
- Système d'étoiles intégré
- Modération avant publication

### 5. Emails Reçus

Tous les emails seront envoyés à **DEUX adresses** :
- **gb_mobile99@outlook.com** (adresse principale)
- **coachalexvohz@gmail.com** (adresse secondaire)

Les emails proviennent de : **noreply@send.gbmobile.ca**

### 6. Validation et Sécurité

- Validation côté client et serveur
- Protection contre le spam
- Validation des formats email
- Messages d'erreur en français/anglais

## Dépannage

### DNS non configurés
Si les DNS ne sont pas encore configurés, les emails ne seront pas envoyés. Vous verrez des erreurs dans les logs.

### Clé API invalide
Vérifiez que la clé API Resend est correcte dans le fichier `.env`.

### Problèmes de formulaires
Les formulaires sont connectés aux APIs suivantes :
- `/api/contact` (POST)
- `/api/booking` (POST)  
- `/api/testimonials` (GET, POST)

---

**Besoin d'aide ?** Consultez le guide officiel de configuration de domaine d'Abacus.AI.
