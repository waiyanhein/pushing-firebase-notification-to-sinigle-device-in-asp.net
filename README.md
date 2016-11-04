# pushing-firebase-notification-to-sinigle-device-in-asp.net

```
public string PushNotifications(string token)
{
      using (var client = new WebClient())
      {
          client.Headers.Add(string.Format("Authorization:key={0}", Utils.FirebaseServerKey)); //get from firebase
          var values = new NameValueCollection();

          values["registration_id"] = token;
          values["data.message"] = "This is the test FCM test message";
          var response = client.UploadValues("https://fcm.googleapis.com/fcm/send", values);
          string responseString = Encoding.Default.GetString(response);
          if (!string.IsNullOrEmpty(responseString))
          {
            return responseString;
          }
          else
          {
             return "Something went wrong";
          }
      }
}
```
