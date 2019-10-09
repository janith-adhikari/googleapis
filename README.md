# Google APIs

## Features
  - Google Place Picker Activity
  - Google Map
  - Google Location
  - Google Place Picker (AutoComplete text View)
### Google Place Activity(Extension)

 start place picker activity
```kotlin
 override fun onClick(v: View?) {
        when (v?.id) {
            R.id.et_address -> {
                startPlacePicker()
            }
        }
} 
```

get result from  **getLocationFromResult(requestCode, resultCode, data)**
```kotlin
override fun onActivityResult(
        requestCode: Int,
        resultCode: Int,
        data: Intent?
    ) {
        super.onActivityResult(requestCode, resultCode, data)
        context?.getLocationFromResult(requestCode, resultCode, data)
            ?.let {
                et_address.setText(it.address)
                latitude = it.latitude
                longtude = it.longtude
            }
    }
```

### Google Place Picker (AutoComplete text View)

Initialize **GooglePlackPickerManager**
```kotlin
    val googlePlacePickerManager = GooglePlacePickerManager(context)
    
    internal fun initPlaceSearch(completeTextView: AutoCompleteTextView) {
        googlePlacePickerManager.initialPlace(
            completeTextView,
            object : GooglePlacePickerCallback() {
                override fun googlePlacePickerCallback(place: Place) {
                    //selected google place
                }
            })
    }
```
***Get Address from LatLng**

```kotlin
    val googlePlacePickerManager = GooglePlacePickerManager(context)
    
    fun...{
        googlePlacePickerManager.initialGeoCode(latlng)
    }

    internal fun initPlaceSearch(completeTextView: AutoCompleteTextView) {
        googlePlacePickerManager.initialPlace(
            completeTextView,
            object : GooglePlacePickerCallback() {
                override fun googleAddressCallback(googleLocation: GoogleLocation) {
                    //
                }
            })
    }
```
