# spark women 
package com.darkness.sparkwomen;
import androidx.appcompat.app.AppCompatActivity; 
import androidx.recyclerview.widget.LinearLayoutManager; 
import androidx.recyclerview.widget.RecyclerView;
import android.app.Dialog; 
import android.content.Intent;
import android.content.SharedPreferences; 
import android.os.Bundle;
import android.view.View; 
import android.view.Window; 
import android.widget.Button; 
import android.widget.EditText;
import android.widget.ImageView; 
import android.widget.TextView; 
import android.widget.Toast; 
import java.util.ArrayList;
import java.util.HashMap; 
import java.util.LinkedHashSet; 
import java.util.Set;
public class ContactActivity extends AppCompatActivity {
EditText contact;

Button addContact;
RecyclerView recyclerView; 
HashMap<String,String> contacts;
ArrayList<String> send; 
ContactsAdapter adapter; 
MyOnClickListener onClickListener; 
ImageView edit;
TextView callerInfo; 
 @Override
public void onBackPressed() { 
 super.onBackPressed();
 startActivity(new  Intent(this,MainActivity.class)); 
 this.finish();
}
@Override
protected void onCreate(Bundle  savedInstanceState) { 
  super.onCreate(savedInstanceState); 
 setContentView(R.layout.activity_contact);
 edit =    findViewById(R.id.editCallButton); 
edit.setOnClickListener(new  View.OnClickListener() {
 @Override
public void onClick(View view) {
 Dialog dialog = new   Dialog(ContactActivity.this);
dialog.requestWindowFeature(Window.FEATURE_NO_TITL 
E);
 dialog.setCancelable(false); 
 dialog.setContentView(R.layout.dialo
 g);
 Button close,save;
close = dialog.findViewById(R.id.dialogCancel); 
save = dialog.findViewById(R.id.dialogSave); 
EditText
number
=
dialog.findViewById(R.id.dialogEditText);
save.setOnClickListener(new 
View.OnClickListener() {
@Override
public void onClick(View view) {
String
numberText
= 
number.getText().toString();
if(numberText.length() == 10){ 
SharedPreferences
sharedPreferences
=
getSharedPreferences("MySharedPref",MODE_PRIVATE);
SharedPreferences.Editor
editor
= 
sharedPreferences.edit();
editor.putString("firstNumber",numberText); 
editor.apply();
setCallingInformation(); 
dialog.dismiss();
}else {
Toast.makeText(ContactActivity.this, "Enter 
valid number!", Toast.LENGTH_SHORT).show();
}
}
});
close.setOnClickListener(new View.OnClickListener() { 
@Override
public void onClick(View view) { 
dialog.dismiss();
}
});dialog.show();
} }); callerInfo = 
findViewById(R.id.callText);
setCallingInformation(); 
contacts = new HashMap<>();
send = new ArrayList<>();
adapter = new ContactsAdapter(this, send, new 
MyOnClickListener() {
@Override
public void onItemClicked(int position) { 
deleteItemFromDatabase(position);
}
});
recyclerView = findViewById(R.id.contacts); 
recyclerView.setAdapter(adapter); 
recyclerView.setLayoutManager(new
LinearLayoutManager(this));
getData();
contact = findViewById(R.id.contactGet); 
addContact = findViewById(R.id.addContact);
addContact.setOnClickListener(new 
View.OnClickListener() {
@Override
sharedPreferences.getString("firstNumber","null");
if 
(firstNumber.isEmpty()||firstNumber.equalsIgnoreCase("null")
){
callerInfo.setText("Please add number.");
}else {
callerInfo.setText(firstNumber);
}
}
private void deleteItemFromDatabase(int position) { 
SharedPreferences
sharedPreferences
=
getSharedPreferences("MySharedPref",MODE_PRIVATE);
Set<String>
oldNumbers
=
sharedPreferences.getStringSet("enumbers",
new 
LinkedHashSet<>());
SharedPreferences.Editor
editor
= 
sharedPreferences.edit();
editor.remove("enumbers"); 
oldNumbers.remove(send.get(position)); 
editor.putStringSet("enumbers",oldNumbers); 
editor.apply();
getData();
}
private void getData() { 
send.clear();
SharedPreferences
sharedPreferences
=
getSharedPreferences("MySharedPref",MODE_PRIVATE); 
Set<String>
oldNumbers
=
sharedPreferences.getStringSet("enumbers",
new
LinkedHashSet<>()); 
send.addAll(oldNumbers); 
adapter.notifyDataSetChanged();
}
}
• Contact Adapter:
package com.darkness.sparkwomen; 
import android.content.Context; 
import android.view.LayoutInflater; 
import android.view.View;
import android.view.ViewGroup; 
import android.widget.ImageView; 
import android.widget.TextView; 
import androidx.annotation.NonNull;
import androidx.recyclerview.widget.RecyclerView; 
import java.util.ArrayList;
import java.util.HashMap;
public
class
ContactsAdapter
extends 
RecyclerView.Adapter<ContactsAdapter.MyViewHolder> {
HashMap<String,String> contacts; 
Context context; 
ArrayList<String> send;
MyOnClickListener myOnClickListener;
class MyViewHolder extends RecyclerView.ViewHolder{
TextView name,contact; 
ImageView delete;
public MyViewHolder(@NonNull View itemView) { 
super(itemView);
contact = itemView.findViewById(R.id.contactItem); 
delete = itemView.findViewById(R.id.deleteIcon);
}
}
}
• Developer Activity: 
package com.darkness.sparkwomen; 
import android.content.Intent;
import androidx.appcompat.app.AppCompatActivity;
public class DeveloperActivity extends AppCompatActivity { 
@Override
public void onBackPressed() { 
super.onBackPressed();
startActivity(new Intent(this,MainActivity.class)); 
this.finish();
 }
} 
Law Displayer Activity:
package com.darkness.sparkwomen;
import androidx.appcompat.app.AppCompatActivity; 
import android.os.Bundle;
import android.view.View; 
import android.widget.Button; 
import android.widget.TextView;
public
class
LawDisplayerActivity
extends 
AppCompatActivity implements View.OnClickListener {
TextView big,oneLine; 
String[] laws, lawsContent; 
int counter;
Button back, next; 
View closeBtn; 
@Override
protected void onCreate(Bundle savedInstanceState) { 
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_law_displayer); 
big = findViewById(R.id.bigLaws);
oneLine = findViewById(R.id.lawString); 
counter = getIntent().getIntExtra("position",0);
laws = new String[]{"The Prohibition of Child Marriage 
Act, 2006","Special Marriage Act, 1954","Dowry Prohibition 
Act, 1961","Indian Divorce Act, 1969","Maternity Benefit 
Act,1861","Medical Termination of Pregnancy 
Act,1971","Sexual Harassment of Women at Workplace
Prevention, Prohibition and Redress) Act, 2013","Indecent 
Representation of Women(Prevention) Act,1986","National 
Commission for Women Act, 1990","Equal Remuneration Act, 
1976"};
lawsContent
=
this.getResources().getStringArray(R.array.lawsBig);
closeBtn = findViewById(R.id.closeBtn); 
closeBtn.setOnClickListener(view -> {
onBackPressed(); 
LawDisplayerActivity.this.finish();
});
back = findViewById(R.id.backBtn); 
next = findViewById(R.id.nextBtn); 
next.setOnClickListener(this); 
back.setOnClickListener(this); 
setData();
}
public void setData(){ 
oneLine.setText(laws[counter]); 
big.setText(lawsContent[counter]);
}
@Override
public void onClick(View view) { 
if(view.getId() == R.id.nextBtn){
if(counter<9){ 
counter++;
}else {
counter = 0;
}
} else if (view.getId() == R.id.backBtn) { 
if(counter == 0){
counter = (laws.length-1);
}else {
counter--;
}
}
setData();
}
}
• Law Model:
package com.darkness.sparkwomen; 
public class LawModel {
String lawString, lawDescription;
public LawModel(String lawString, String lawDescription)
{
this.lawString = lawString; 
this.lawDescription = lawDescription;
}
public LawModel() {
}
LawsActivity.this.finish();
}
@Override
protected void onCreate(Bundle savedInstanceState) { 
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_laws);
RecyclerView
recyclerView
= 
findViewById(R.id.recycleLaws);
String[] laws = new String[]{"The Prohibition of Child 
Marriage Act, 2006","Special Marriage Act, 1954","Dowry 
Prohibition Act, 1961","Indian Divorce Act, 1969","Maternity 
Benefit Act,1861","Medical Termination of Pregnancy 
Act,1971","Sexual Harassment of Women at Workplace 
(Prevention, Prohibition and Redress) Act, 2013","Indecent 
Representation of Women(Prevention) Act,1986","National 
Commission for Women Act, 1990","Equal Remuneration Act, 
1976"};
-> {
MyAdapter adapter = new MyAdapter(this, laws, position
Intent
intent
=
new
Intent(LawsActivity.this,LawDisplayerActivity.class); 
intent.putExtra("position",position); 
startActivity(intent);
});
recyclerView.setAdapter(adapter); 
recyclerView.setLayoutManager(new
LinearLayoutManager(this)); 
findViewById(R.id.backBtn).setOnClickListener(view ->
{
startActivity(new 
Intent(LawsActivity.this,MainActivity.class));
LawsActivity.this.finish();
});
}
}
• Main Activity:
package com.darkness.sparkwomen;
import androidx.appcompat.app.AppCompatActivity; 
import androidx.core.app.ActivityCompat;
import android.Manifest; 
import android.content.Intent;
import android.content.SharedPreferences; 
import android.content.pm.PackageManager; 
import android.net.Uri;
import android.os.Bundle;
import android.telephony.SmsManager; 
import android.view.View;
import android.widget.Button; 
import
com.google.android.gms.location.FusedLocationProviderClient;
import com.google.android.gms.location.LocationServices; 
import java.util.HashSet;
import java.util.Set;
public class MainActivity extends AppCompatActivity
getSharedPreferences("MySharedPref",MODE_PRIVATE); 
Set<String>
oldNumbers
=
sharedPreferences.getStringSet("enumbers",
new
HashSet<>());
if(!oldNumbers.isEmpty()){ 
for(String ENUM : oldNumbers)
manager.sendTextMessage(ENUM,null,"Im
in 
Trouble!\nSending My Location :\n"+myLocation,null,null);
}
}
}
• My Adapter:
package com.darkness.sparkwomen; 
import android.content.Context; 
import android.view.LayoutInflater; 
import android.view.View;
import android.view.ViewGroup; 
import android.widget.TextView;
import androidx.annotation.NonNull;
import androidx.recyclerview.widget.RecyclerView;
public
class
MyAdapter
extends 
RecyclerView.Adapter<MyAdapter.MyViewHolder>{
String[] laws;
Context context;
MyOnClickListener myOnClickListener;
public MyAdapter(Context context, String[] laws, 
MyOnClickListener onClickListener){
this.laws = laws; 
this.context = context;
this.myOnClickListener = onClickListener;
}
@NonNull 
@Override
public MyViewHolder onCreateViewHolder(@NonNull 
ViewGroup parent, int viewType) {
return
new
MyViewHolder(LayoutInflater.from(context).inflate(R.layout.l 
aw_item,parent,false));
}
@Override
public void onBindViewHolder(@NonNull MyViewHolder 
holder, int position) {
int newPosition = position + 1;
String displayString = newPosition + " " + laws[position]; 
holder.law.setText(displayString); 
holder.law.setOnClickListener(view
->
myOnClickListener.onItemClicked(position));
}
@Override
public int getItemCount() { 
return laws.length;
}
static
class
MyViewHolder
extends
RecyclerView.ViewHolder{
TextView law;
public MyViewHolder(@NonNull View itemView) { 
super(itemView);
law = itemView.findViewById(R.id.lawItem);
}
}
}
Self Defence Activity:
package com.darkness.sparkwomen; 
import android.os.Bundle;
import android.webkit.WebChromeClient; 
import android.webkit.WebView;
import android.webkit.WebViewClient;
import androidx.appcompat.app.AppCompatActivity;
public class SelfDefenseActivity extends AppCompatActivity
{
WebView webView; 
@Override
protected void onCreate(Bundle savedInstanceState) { 
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_self_defense); 
webView = findViewById(R.id.webView); 
webView.setWebChromeClient(new
WebChromeClient());
webView.getSettings().setLoadsImagesAutomatically(true); 
webView.getSettings().setJavaScriptEnabled(true);
webView.loadUrl("https://www.youtube.com/embed/T7aNSR
oDCmg");
}
}
• Service Mine:
package com.darkness.sparkwomen; 
import android.Manifest;
import android.app.Notification;
import android.app.NotificationChannel; 
import android.app.NotificationManager; 
import android.app.PendingIntent; 
import android.app.Service;
import android.content.Context; 
import android.content.Intent;
import android.content.SharedPreferences; 
import android.content.pm.PackageManager; 
import android.location.Location;
import android.media.MediaPlayer; 
import android.os.Build;
import android.os.IBinder;
import android.telephony.SmsManager; 
import android.view.View;
import androidx.annotation.Nullable; 
import androidx.core.app.ActivityCompat; 
import
com.github.tbouron.shakedetector.library.ShakeDetector;
/
@Override
//
public void onClick(View view) {
//
mediaPlayer.start();
//
//
//
SharedPreferences sharedPreferences = 
getSharedPreferences("MySharedPref",MODE_PRIVATE);
//
Set<String> oldNumbers =
sharedPreferences.getStringSet("enumbers",
new 
HashSet<>());
//
if(!oldNumbers.isEmpty()){
//
for(String ENUM : oldNumbers)
//
manager.sendTextMessage(ENUM,null,"Im in 
Trouble!\nSending My Location :\n"+myLocation,null,null);
//
}
//
//
}
//
});
//
//
windowManager.addView(view,params);
ShakeDetector.create(this, () -> { 
mediaPlayer.start();
SharedPreferences
sharedPreferences
= 
getSharedPreferences("MySharedPref",MODE_PRIVATE);
Set<String>
oldNumbers
=
sharedPreferences.getStringSet("enumbers",
new 
HashSet<>());
if(!oldNumbers.isEmpty()){ 
for(String ENUM : oldNumbers)
manager.sendTextMessage(ENUM,null,"Im
in 
Trouble!\nSending My Location :\n"+myLocation,null,null);
}
});
}
@Override
public int onStartCommand(Intent intent, int flags, int 
startId) {
if (intent.getAction().equalsIgnoreCase("STOP")) { 
if(isRunning){
mediaPlayer.stop(); 
this.stopForeground(true); 
this.stopSelf();
//
windowManager.removeView(view); 
isRunning = false;
}
} else {
Intent notificationIntent = new Intent(this, 
SmsActivity.class);
PendingIntent
pendingIntent
= 
PendingIntent.getActivity(this, 0, notificationIntent, 
PendingIntent.FLAG_MUTABLE);
if
(Build.VERSION.SDK_INT
>=
@Override
public void onDestroy() { 
mediaPlayer.stop(); 
mediaPlayer.release();
super.onDestroy();
}
}
• Sms Activity:
package com.darkness.sparkwomen;
import androidx.appcompat.app.AppCompatActivity; 
import androidx.core.content.ContextCompat;
import android.Manifest; 
import android.content.Intent;
import android.content.pm.PackageManager;
import com.google.android.material.snackbar.Snackbar; 
public class SmsActivity extends AppCompatActivity { 
Button start,stop;
@Override
public void onBackPressed() { 
super.onBackPressed(); 
startActivity(new
Intent(SmsActivity.this,MainActivity.class));
}
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_sms); 
stop = findViewById(R.id.stopService);
start
=
findViewById(R.id.startService); 
start.setOnClickListener(this::startServiceV);
stop.setOnClickListener(this::stopService);
}
public void stopService(View view) {
Intent
notificationIntent
=
new
Intent(this,ServiceMine.class);
notificationIntent.setAction("stop");
if
(Build.VERSION.SDK_INT
>= 
Build.VERSION_CODES.O) {
if(ServiceMine.isRunning){
getApplicationContext().startForegroundService(notificationIn 
tent);
Snackbar.make(findViewById(android.R.id.content),"Service 
Stopped!", Snackbar.LENGTH_LONG).show();
}
}else {
if(ServiceMine.isRunning){
// 
getApplicationContext().startService(notificationIntent);
getApplicationContext().startService(notificationIntent);
Snackbar.make(findViewById(android.R.id.content),"Service
if

(Build.VERSION.SDK_INT

>= 

Build.VERSION_CODES.O) {

getApplicationContext().startForegroundService(notificationIn 

tent);

Snackbar.make(findViewById(android.R.id.content),"Service 

Started!", Snackbar.LENGTH_LONG).show();

}else {

getApplicationContext().startService(notificationIntent);

Snackbar.make(findViewById(android.R.id.content),"Service 

Started!", Snackbar.LENGTH_LONG).show();

}

} }}

• Splash Activity:

package com.darkness.sparkwomen;

import androidx.appcompat.app.AppCompatActivity; 

import androidx.core.app.ActivityCompat;

import android.Manifest; 

import android.content.Intent;

import android.content.pm.PackageManager; 

import android.location.Location;

import android.os.Bundle; 

import android.widget.Toast;

import com.google.android.gms.location.LocationCallback; 

import com.google.android.gms.location.LocationRequest;
import com.google.android.gms.location.LocationResult; 
import com.google.android.gms.location.LocationServices; 
import com.karumi.dexter.Dexter;
import com.karumi.dexter.MultiplePermissionsReport; 
import com.karumi.dexter.PermissionToken;
import com.karumi.dexter.listener.PermissionRequest; 
import
com.karumi.dexter.listener.multi.MultiplePermissionsListener;
import java.util.List;
public class SplashActivity extends AppCompatActivity { 
boolean isAllPermissionsGranted = false;
@Override
protected void onCreate(Bundle savedInstanceState) { 
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_splash); 
requestPermission();
findViewById(R.id.btnGetStarted).setOnClickListener(view ->
{
if(isAllPermissionsGranted){ 
startActivity(new
Intent(SplashActivity.this,MainActivity.class));
SplashActivity.this.finish();
}else {
Toast.makeText(this,
"Please grant required permissions!", Toast.LENGTH_SHORT).show();
requestPermission();
}

}
LocationServices.getFusedLocationProviderClient(SplashActi 
vity.this).requestLocationUpdates(mLocationRequest, 
mLocationCallback, null);
}
}
XML File :-
• Activity_contact:
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent" 
android:layout_height="match_parent" 
tools:context=".ContactActivity">
<View
android:layout_width="100dp" 
android:layout_height="100dp"
android:background="@drawable/top_left_corner_oval"/>
<RelativeLayout 
android:layout_above="@id/callingInfo" 
android:layout_centerVertical="true" 
android:layout_width="wrap_content" 
android:layout_height="wrap_content">
:"/>
android:text="Call will be placed to following number
<TextView 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:id="@+id/callText" 
android:text=""/>
</LinearLayout>
<ImageView 
android:id="@+id/editCallButton" 
android:layout_alignTop="@id/callingInfo"
android:layout_alignBottom="@id/callingInfo" 
android:layout_width="wrap_content" 
android:layout_marginEnd="20dp" 
android:layout_above="@id/bottomLayout" 
android:layout_alignParentEnd="true" 
android:layout_height="wrap_content" 
android:src="@drawable/ic_baseline_edit_24"/>
<RelativeLayout 
android:layout_margin="20dp" 
android:id="@+id/bottomLayout" 
android:layout_centerHorizontal="true" 
android:layout_alignParentBottom="true" 
android:layout_width="wrap_content" 
android:layout_height="100dp">
<EditText
android:layout_width="200dp
android:layout_height="wrap_content" 

android:hint="Number" 

android:layout_alignTop="@id/addContact" 

android:layout_marginEnd="10dp" 

android:id="@+id/contactGet"/>

<Button 

android:id="@+id/addContact"

android:layout_alignParentBottom="true" 

android:layout_width="wrap_content" 

android:layout_height="wrap_content" 

android:layout_toRightOf="@id/contactGet" 

android:text="Add"/>

</RelativeLayout>

</RelativeLayout>

• activity_law_displayer:

<?xml version="1.0" encoding="utf-8"?>

<RelativeLayout 

xmlns:android="http://schemas.android.com/apk/res/android"

xmlns:app="http://schemas.android.com/apk/res-auto"

xmlns:tools="http://schemas.android.com/tools"

android:layout_width="match_parent" 

android:layout_height="match_parent" 

tools:context=".LawDisplayerActivity">

<View

android:layout_width="30dp" 

android:layout_height="30dp" 

android:layout_alignParentStart="true"
app:layout_constraintEnd_toEndOf="parent" 
app:layout_constraintStart_toStartOf="parent" 
android:layout_marginHorizontal="50dp" 
android:layout_centerHorizontal="true" 
android:layout_below="@id/imgLaw" 
android:textStyle="bold" 
android:id="@+id/lawString"
/>
<TextView
android:layout_width="match_parent" 
android:layout_height="wrap_content"
app:layout_constraintBottom_toTopOf="@+id/lastLinear" 
app:layout_constraintTop_toBottomOf="@id/lawString" 
android:id="@+id/bigLaws"
android:padding="20dp" 
android:background="@drawable/purple_background" 
android:layout_below="@id/lawString" 
android:text="According to the International Research
Centre for Women, almost 47 percent of girls are married
before the age of 18. Currently, India ranks 13 in the world 
when it comes to child marriages. Since child marriage has 
been steeped into the Indian culture and tradition since 
centuries, it has been tough eliminating it.
The Prohibition of Child Marriage Act was made effective in 
2007. This act defines child marriage as a marriage where the 
groom or the bride are underage, that is, the bride is under 18 
years of age or the boy is younger than 21 years.Parents trying 
to marry underage girls are subject to action under this law.
Since the law makes these marriages illegal, it acts as a major 
deterrent."
android:layout_marginTop="10dp" 
android:layout_above="@id/lastLinear" 
android:layout_marginHorizontal="50dp"/>
<LinearLayout 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:id="@+id/lastLinear" 
android:layout_alignParentBottom="true" 
android:layout_centerHorizontal="true" 
app:layout_constraintBottom_toBottomOf="parent" 
android:layout_marginBottom="40dp" 
android:orientation="horizontal">
<Button
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Back" 
app:layout_constraintEnd_toEndOf="parent" 
app:layout_constraintStart_toStartOf="parent" 
android:id="@+id/backBtn" 
android:textStyle="bold"
/>
<Button
android:layout_marginStart="10dp" 
android:layout_width="wrap_content" 
android:layout_height="wrap_content
android:text="Next" 
app:layout_constraintEnd_toEndOf="parent" 
app:layout_constraintStart_toStartOf="parent" 
android:id="@+id/nextBtn" 
android:textStyle="bold"
/>
</LinearLayout>
</RelativeLayout>
• Activity_laws:
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent" 
android:layout_height="match_parent" 
tools:context=".LawsActivity">
<View 
android:id="@+id/topleftoval" 
android:layout_width="150dp" 
android:layout_height="150dp"
android:background="@drawable/top_left_corner_oval" 
app:layout_constraintTop_toTopOf="parent" 
app:layout_constraintStart_toStartOf="parent" />
android:text="Next" 

app:layout_constraintEnd_toEndOf="parent" 

app:layout_constraintStart_toStartOf="parent" 

android:id="@+id/nextBtn" 

android:textStyle="bold"

/>

</LinearLayout>

</RelativeLayout>

• Activity_laws:

<?xml version="1.0" encoding="utf-8"?>

<RelativeLayout 

xmlns:android="http://schemas.android.com/apk/res/android"

xmlns:app="http://schemas.android.com/apk/res-auto"

xmlns:tools="http://schemas.android.com/tools"

android:layout_width="match_parent" 

android:layout_height="match_parent" 

tools:context=".LawsActivity">

<View 

android:id="@+id/topleftoval" 

android:layout_width="150dp" 

android:layout_height="150dp"

android:background="@drawable/top_left_corner_oval" 

app:layout_constraintTop_toTopOf="parent" 

app:layout_constraintStart_toStartOf="parent" />
<ImageView

android:layout_width="150dp" 

android:layout_height="150dp"

android:src="@drawable/laws" 

android:layout_below="@id/topleftoval" 

android:layout_centerHorizontal="true" 

app:layout_constraintTop_toBottomOf="@id/topleftoval" 

android:layout_marginTop="-40dp" 

android:id="@+id/imgLaw" 

app:layout_constraintStart_toStartOf="parent" 

app:layout_constraintEnd_toEndOf="parent"/>

<TextView

android:layout_width="wrap_content" 

android:layout_height="wrap_content" 

android:text="Basic Laws for Women!" 

app:layout_constraintTop_toBottomOf="@id/imgLaw" 

app:layout_constraintEnd_toEndOf="parent" 

app:layout_constraintStart_toStartOf="parent" 

android:layout_centerHorizontal="true" 

android:layout_below="@id/imgLaw" 

android:textStyle="bold"

android:id="@+id/layText"

/>

<androidx.recyclerview.widget.RecyclerView 

android:layout_width="match_parent" 

android:layout_height="wrap_content" 

app:layout_constraintBottom_toTopOf="@+id/backBtn" 

app:layout_constraintTop_toBottomOf="@id/layText" 
android:fontFamily="cursive" 

android:gravity="center_horizontal" 

android:text="Spark Women" 

android:textColor="#FFFFFFFF" 

android:textSize="50dp" />

<RelativeLayout 

android:id="@+id/relativeLayout" 

android:layout_width="341dp" 

android:layout_height="401dp"

android:layout_centerInParent="true">

<LinearLayout

android:id="@+id/first" 

android:layout_width="150dp" 

android:layout_height="150dp" 

android:layout_marginRight="50dp" 

android:background="@drawable/oval_purple_full" 

android:clickable="true"

android:focusable="true" 

android:gravity="center" 

android:orientation="vertical">

<ImageView 

android:layout_width="82dp" 

android:layout_height="76dp" 

android:layout_gravity="center" 

android:src="@drawable/girll" />

<TextView 

android:layout_width="wrap_content
<LinearLayout 

android:id="@+id/third" 

android:layout_width="150dp" 

android:layout_height="150dp" 

android:layout_below="@id/first" 

android:layout_marginTop="50dp" 

android:layout_marginRight="50dp"

android:background="@drawable/oval_purple_full" 

android:clickable="true"

android:focusable="true" 

android:gravity="center" 

android:orientation="vertical" 

android:visibility="gone">

<ImageView

android:layout_width="50dp" 

android:layout_height="50dp" 

android:layout_gravity="center" 

android:src="@drawable/settings" />

<TextView

android:layout_width="wrap_content" 

android:layout_height="wrap_content" 

android:layout_gravity="center" 

android:text="Settings" />

</LinearLayout>

<LinearLayout

android:id="@+id/fourth" 

android:layout_width="150dp
android:layout_height="150dp" 
android:layout_below="@id/second" 
android:layout_marginTop="50dp" 
android:layout_toRightOf="@id/third" 
android:background="@drawable/oval_purple_full" 
android:clickable="true"
android:focusable="true" 
android:gravity="center" 
android:orientation="vertical">
<ImageView
android:layout_width="102dp" 
android:layout_height="99dp" 
android:layout_gravity="center" 
android:src="@drawable/img_18" />
<TextView
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:layout_gravity="center" 
android:text="Basic Laws" />
</LinearLayout>
<LinearLayout 
android:id="@+id/fifth" 
android:layout_width="150dp" 
android:layout_height="150dp"
android:layout_below="@id/second" 
android:layout_marginTop="50dp" 
android:layout_toRightOf="@id/first"
android:background="@drawable/oval_purple_full" 
android:clickable="true"
android:focusable="true" 
android:gravity="center" 
android:orientation="vertical">
<ImageView 
android:layout_width="150dp" 
android:layout_height="101dp" 
android:layout_gravity="center" 
android:src="@drawable/pngegg" />
<TextView
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:layout_gravity="center" 
android:text="Self Defence" />
</LinearLayout>
</RelativeLayout>
<LinearLayout 
android:layout_width="match_parent" 
android:layout_height="wrap_content"
android:layout_below="@+id/relativeLayout" 
android:layout_marginTop="20dp" 
android:id="@+id/linear1" 
android:gravity="center_horizontal">
<Button
android:id="@+id/developer" 
android:layout_width="wrap_content"
Developed_by:
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent" 
android:layout_height="match_parent" 
android:orientation="vertical" 
tools:context=".DeveloperActivity" 
android:background="@drawable/img_20"
>
<RelativeLayout 
android:layout_width="match_parent" 
android:layout_height="wrap_content" 
android:layout_marginRight="20dp" 
android:layout_marginLeft="20dp">
</RelativeLayout>
<androidx.cardview.widget.CardView 
android:layout_width="match_parent" 
android:layout_height="173dp" 
android:layout_marginLeft="30dp" 
android:layout_marginTop="30dp" 
android:layout_marginRight="30dp" 
app:cardCornerRadius="8dp">
<LinearLayout
android:layout_width="match_parent
android:layout_height="match_parent" 
android:background="@drawable/bg1" 
android:orientation="horizontal">
<LinearLayout
android:layout_width="match_parent" 
android:layout_height="wrap_content" 
android:layout_marginLeft="30dp" 
android:layout_marginTop="20dp" 
android:layout_marginRight="30dp" 
android:orientation="vertical">
<LinearLayout
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:orientation="vertical">
<TextView
<TextView
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Shubhangi Nimbalkar" 
android:textColor="@color/black" 
android:textSize="25dp" /
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Coding Contribution"
android:textSize="15dp" />
</LinearLayout>
<RelativeLayout
android:layout_width="match_parent" 
android:layout_height="match_parent">
<ImageView
android:layout_width="80dp" 
android:layout_height="100dp" 
android:layout_alignParentRight="true" 
android:src="@drawable/img_21" />
</RelativeLayout>
</LinearLayout>
</LinearLayout>
</androidx.cardview.widget.CardView>
<androidx.cardview.widget.CardView 
android:layout_width="match_parent" 
android:layout_height="173dp" 
android:layout_marginLeft="30dp" 
android:layout_marginTop="30dp" 
android:layout_marginRight="30dp" 
app:cardCornerRadius="8dp">
<LinearLayout 
android:layout_width="match_parent" 
android:layout_height="match_parent" 
android:background="@drawable/bg2" 
android:orientation="horizontal">
<LinearLayout 
android:layout_width="match_parent" 
android:layout_height="wrap_content" 
android:layout_marginLeft="30dp
android:layout_marginTop="20dp" 
android:layout_marginRight="30dp" 
android:orientation="vertical">
<LinearLayout
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:orientation="vertical">
<TextView
<TextView
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Mahek Sayyad" 
android:textColor="@color/black" 
android:textSize="25dp" />
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Designing Contribution" 
android:textSize="15dp" />
</LinearLayout>
<RelativeLayout 
android:layout_width="match_parent" 
android:layout_height="match_parent">
<ImageView
android:layout_width="80dp" 
android:layout_height="100dp" 
android:layout_alignParentRight="true" 
android:src="@drawable/img_22" />
</RelativeLayout>
</LinearLayout>
</LinearLayout>
</androidx.cardview.widget.CardView>
<androidx.cardview.widget.CardView 
android:layout_width="match_parent" 
android:layout_height="173dp" 
android:layout_marginLeft="30dp" 
android:layout_marginTop="30dp" 
android:layout_marginRight="30dp" 
app:cardCornerRadius="8dp">
<LinearLayout
android:layout_width="match_parent" 
android:layout_height="match_parent" 
android:background="@drawable/bg3" 
android:orientation="horizontal"
<LinearLayout
android:layout_width="match_parent" 
android:layout_height="wrap_content" 
android:layout_marginLeft="30dp" 
android:layout_marginTop="20dp" 
android:layout_marginRight="30dp" 
android:orientation="vertical">
<LinearLayout 
android:layout_width="wrap_content" 
android:layout_height="wrap_content"
android:orientation="vertical">
<TextView 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Prachi Shete" 
android:textColor="@color/black" 
android:textSize="25dp" />
<TextView 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Testing Contribution" 
android:textSize="15dp" />
</LinearLayout>
<RelativeLayout 
android:layout_width="match_parent" 
android:layout_height="match_parent">
<ImageView
android:layout_width="80dp" 
android:layout_height="100dp" 
android:layout_alignParentRight="true" 
android:src="@drawable/img_23" />
</RelativeLayout>
</LinearLayout>
</LinearLayout>
</androidx.cardview.widget.CardView>
/LinearLayout>

