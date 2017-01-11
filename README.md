# CustomDialog
## CustomDialog에서 입력한 문자를 Firebase Database에 업로드
![Alt text](https://github.com/DianaLeee/CustomDialog/blob/master/%ED%95%9C%EC%9D%B4%EC%9D%8C%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8.PNG?raw=true)
### 1.1 OptionMenu & CustomDialog
<pre>
 <code>
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.menu_test, menu);
        return true;
    }
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        showChangeLangDialog();
        return true;
    }
    public void showChangeLangDialog() {
        AlertDialog.Builder dialogBuilder = new AlertDialog.Builder(this);
        LayoutInflater inflater = this.getLayoutInflater();
        final View dialogView = inflater.inflate(R.layout.custom_dialog, null);
        dialogBuilder.setView(dialogView);

        dialogBuilder.setTitle("Add new string");
        dialogBuilder.setMessage("");
        dialogBuilder.setPositiveButton("ADD", new DialogInterface.OnClickListener() {
          
        });
        dialogBuilder.setNegativeButton("Cancel", new DialogInterface.OnClickListener() {
            public void onClick(DialogInterface dialog, int whichButton) {
                //pass
            }
        });
        AlertDialog b = dialogBuilder.create();
        b.show();
    }
    </code>
</pre>
   
### 1.2 Firebase
<pre>
 <code>
FirebaseDatabase.getInstance();
private DatabaseReference myRef = database.getReference("text");

ValueEventListener() {
            @Override
            public void onDataChange(DataSnapshot dataSnapshot) {
                String value = dataSnapshot.getValue(String.class);
                Log.d(TAG, "Value is: " + value);
                mTextView.setText(value);
            }
            @Override
            public void onCancelled(DatabaseError error) {
                // Failed to read value
                Log.w(TAG, "Failed to read value.", error.toException());
            }
        });
</code>
</pre>
