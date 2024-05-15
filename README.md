<html>
<head>
  <h1>MAXś Space</h1>
<script src="https://cdn.onesignal.com/sdks/web/v16/OneSignalSDK.page.js" defer></script>
<script>
   window.OneSignalDeferred = window.OneSignalDeferred || [];
  OneSignalDeferred.push(function(OneSignal) {
    OneSignal.init({
      appId: "f11399dd-e198-41a0-8aae-a2a6e1448ad5",
OneSignal.login("externalID");
console.log('Logged in');
OneSignal.User.PushSubscription.id(function(userId) {
console.log("OneSignal user ID:", userId);
var settings = {
"url": "https://api.onesignal.com/apps/f11399dd-e198-41a0-8aae-a2a6e1448ad5/subscriptions/"+ userId +"/user/identity",
"method": "GET",
"timeout": 5,
};
});
});
</script>
</head>
<body>
<h1>Hi Stranger</h1>
</body>
</html>
