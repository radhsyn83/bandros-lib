# Custom Utils

[![Release](https://jitpack.io/v/jitpack/android-example.svg)](https://jitpack.io/#radhsyn83/bandros-lib)

# Getting Started

Add this to your dependencies.

```gradle
dependencies {
  implementation 'com.github.radhsyn83:bandros-lib:v1.1.8'
}
```

# #Form Validation
#### Function
```java
BFormControl().formValidation(/*Context*/, /*ArrayList<FormValidationModel>*/, /*FormValidationListener*/)
```
#### Model
```java
BFormModel(/*editText*/,/*Form Name*/,/*Min Length*/,/*Max Length*/,/*Form Type*/,/*editText(To confirm like re-password)*/)
```
#### Form Type
```java
BFormControl.TYPE_NORMAL
BFormControl.TYPE_EMAIL
```
#### Listener
```java
BFormControl.OnFormControlListener{
    override fun onFailed(errorModel: BFormModel, msg: String) {
        // Invalid message here
    }

    override fun onSuccess() {
        // Function all form valid
    }
})
.check()
```
#### Example

```java
val phone = this.findViewById<EditText>(R.id.et_phone)
val newPassword = this.findViewById<EditText>(R.id.et_new_password)
val newPasswordVer = this.findViewById<EditText>(R.id.et_new_password_verification)

val phoneCheck = BFormModel(newPassword,"Phone",3)
val passwordCheck = BFormModel(newPassword,"Password",3,null,BFormControl.TYPE_NORMAL,newPasswordVer)

//FORM VALIDATION
BFormControl().init(ctx)
    .addForm(passwordCheck)
    .listener(object : BFormControl.OnFormControlListener {
        override fun onFailed(errorModel: BFormModel, msg: String) {
            //On Form invalid
            toast(msg)
            /*if phone empty will show "Phone cant be empty"*/
        }

        override fun onSuccess() {
            //do your job
        }
    })
    .check()
```


# #Composite Form
![Image](https://github.com/radhsyn83/bandros-lib/blob/master/images/Example%20composite%20Form.png)

```java
<com.segamedev.bandros.BFormInputText
    android:id="@+id/formInput"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    app:b_formName="No. HP"
    app:b_formHint="Masukkan nomor hp"
    app:b_leftButtonShow="true"
    app:b_rightButtonShow="true"
    app:b_formNameColor="@color/colorAccent"
    app:b_formHintColor="@android:color/darker_gray"/>
```

You must use the following properties in your XML to change your CircularImageView.

| Properties                   | Type                         | Default   |
| ---------------------------- | ---------------------------- | --------- |
| `app:b_formName`             | string                       | Form Name |
| `app:b_formNameColor`        | color                        | #4aa9e9   |
| `app:b_formHint`             | string                       | Form Hint |
| `app:b_formHintColor`        | color                        | #ccc      |
| `app:b_leftButtonShow`       | boolean                      | false     |
| `app:b_leftButtonIcon`       | drawable                     | s         |
| `app:b_leftButtonIconTint`   | color                        | #000      |
| `app:b_rightButtonShow`      | boolean                      | false     |
| `app:b_rightButtonIcon`      | drawable                     | s         |
| `app:b_rightButtonIconTint`  | color                        | #000      |
| `app:b_formReadOnly`         | boolean                      | false     |
| `app:b_formInputType`        | text, phone, email, textarea | text      |

# OnClickListener
```java
formInput.onLeftButtonClick {
    Toast.makeText(this, "Left Button clicked", Toast.LENGTH_LONG).show()
}

formInput.onRightButtonClick {
    Toast.makeText(this, "Right Button clicked", Toast.LENGTH_LONG).show()
}
```
# Get Form title and Form input
```java
//Get Form Text
val text: String = formInput.getText()

//Form Input
val fInput: EditText = formInput.getFormInput()

//Form Title
val fTitle: TextView = formInput.getFormTitle()
```
