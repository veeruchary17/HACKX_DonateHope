# DonateHope - Seed Data Instructions

To populate your database with sample orphanages and data for testing:

1. **Create Admin Account**
   - Register a new account as type 'donor'
   - Manually update the user type to 'admin' in the Supabase dashboard:
     ```sql
     UPDATE profiles SET user_type = 'admin' WHERE email = 'admin@donatehope.org';
     ```

2. **Create Sample Orphanages**
   - Register 3-5 accounts as orphanage type
   - Fill in details like name, location, children count
   - Each will automatically get a unique QR code

3. **Verify Orphanages**
   - As admin, update orphanages to verified status:
     ```sql
     UPDATE orphanages SET verified = true;
     ```

4. **Add Sample Needs**
   - Login as each orphanage account
   - Go to the orphanage dashboard
   - Add various needs (food, clothes, books, etc.) with different urgency levels

5. **Create Sample Events**
   - In the orphanage dashboard, add upcoming events
   - Include fundraisers, volunteer events, birthday drives, etc.

6. **Test Donations**
   - Register a donor account
   - Browse orphanages and make test donations
   - Check the orphanage dashboard to see donations appear

## Quick SQL for Sample Data

```sql
-- Example: Add sample needs after creating orphanages
INSERT INTO needs (orphanage_id, category, item_name, description, quantity, urgency)
VALUES
  ((SELECT id FROM orphanages LIMIT 1), 'food', 'Rice bags', 'We need rice for monthly supplies', '50 kg', 'high'),
  ((SELECT id FROM orphanages LIMIT 1), 'clothes', 'Winter jackets', 'Cold season approaching', '20 pieces', 'critical'),
  ((SELECT id FROM orphanages LIMIT 1), 'books', 'School textbooks', 'For grade 5-8 students', '30 books', 'medium');
```

This will help you test all features of the platform!
