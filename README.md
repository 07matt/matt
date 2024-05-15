<html>
<head>
  <h1>MAXś Space</h1>
<script src="https://cdn.onesignal.com/sdks/web/v16/OneSignalSDK.page.js" defer></script>
<script>
   window.OneSignalDeferred = window.OneSignalDeferred || [];
  OneSignalDeferred.push(function(OneSignal) {
    OneSignal.init({
      appId: "f11399dd-e198-41a0-8aae-a2a6e1448ad5",
    });
  });
setTimeout(function(){
console.log("about to initialize OneSignal");
window._oneSignalInitOptions = {
promptOptions: {
slidedown: {
prompts: [
{
type: "push",
autoPrompt: true,
text: {
actionMessage: "Subscribe to Notifications!",
acceptButton: "Yes",
cancelButton: "No",
},
delay: {
timeDelay: 1,
pageViews: 1,
}
}
]
}
}
};

window.OneSignal = window.OneSignal || [];
window.OneSignal.push(function() {
window.OneSignal.init(window._oneSignalInitOptions);
console.log('OneSignal Initialized');
OneSignal.login("externalID");
console.log('Logged in');
OneSignal.User.PushSubscription.id(function(userId) {
console.log("OneSignal user ID:", userId);
var settings = {
"url": "https://api.onesignal.com/apps/f11399dd-e198-41a0-8aae-a2a6e1448ad5/subscriptions/"+ userId +"/user/identity",
"method": "GET",
"timeout": 5,
};

jQuery.ajax(settings).done(function (response) {
var oneSignalId = response.identity.onesignal_id;
//console.log(response.identity.onesignal_id);

jQuery('#storeSelect').change(function() {
var selectedStore = jQuery(this).val();
updateOneSignalStore(selectedStore, oneSignalId);
});
});
}).catch((error) => {
console.error("Error getting OneSignal user ID:", error);
});
​
});
}, 3000);


function updateOneSignalStore(store, onesignalId) {
var data = {
'action': 'onesignal_update_tags',
'onesignalId': onesignalId,
'storeId': store
};

jQuery.ajax({
url: '/wp-admin/admin-ajax.php',
type: 'POST',
data: data,
success: function(response) {
console.log(response); // Handle the response here
}
});
}
</script>
 
</head>
 
<body>

<h1>Hi Stranger</h1>
  
 
</body>
</html>
