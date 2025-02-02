# Inkam
Ernning mony
+ "\"currency\": \"BDT\","
                    + "\"phone_number\": \"YOUR_PHONE_NUMBER\","
                    + "\"transaction_id\": \"TRANSACTION_ID\""
                    + "}";
            
            // রিকোয়েস্ট পাঠানোর জন্য আউটপুট স্ট্রিম সেটআপ
            con.setDoOutput(true);
            try (OutputStream os = con.getOutputStream()) {
                byte[] input = jsonInputString.getBytes("utf-8");
                os.write(input, 0, input.length);
            }
            
            // সার্ভারের রেসপন্স প্রাপ্তি
            int responseCode = con.getResponseCode();
            System.out.println("HTTP Response Code: " + responseCode);
            
            // সার্ভার থেকে রেসপন্স গ্রহণ
            if (responseCode == HttpURLConnection.HTTP_OK) {
                System.out.println("Payment Success");
            } else {
                System.out.println("Payment Failed");
            }
            
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

৫. *Callback URL এবং Transaction Confirmation*:
বিকাশ API এর মাধ্যমে পেমেন্ট সফল হওয়ার পর, সাধারণত বিকাশ তোমাকে একটি *callback URL* প্রদান করবে যেখানে পেমেন্টের অবস্থা পাঠানো হবে (যেমন, সফল হয়েছে, ব্যর্থ হয়েছে)।

৬. *Firebase বা Backend Integration*:![Screenshot_20250122-191200](https://github.com/user-attachments/assets/aa3a2b51-43d4-419e-b856-bc297c5dd0f9)
