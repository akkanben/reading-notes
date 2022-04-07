# Reading Notes 39 -- Location

From [Android Docs](https://developer.android.com/training/location/retrieve-current)

To get the last known location of a device we can use the "fused location provider". This is part of the Google Play API and requires adding the services component in the build.gradle file.

Permissions are requred for using the location provider and require adding permissions for location in the manifest file.

The activity using the location requires an instance of the Fused Location Provider Client in the `onCreate()`:

```java
private FusedLocationProviderClient fusedLocationClient;

@Override
protected void onCreate(Bundle savedInstanceState) {

    fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);
}
```

There are two methods for getting location information from the fusedLocationClient instance:

- `getLastLocation()` a quick and battery efficient last location however it could be old depending on a few factors.
- `getCurrentLocation()` a more consistent and accurate location request.
  - `requestLocationUpdates()` can also make sure that the request is as fresh as possible at the expense of battery.

Example:

```java
fusedLocationClient.getLastLocation()
        .addOnSuccessListener(this, new OnSuccessListener<Location>() {
            @Override
            public void onSuccess(Location location) {
                // Got last known location. In some rare situations this can be null.
                if (location != null) {
                    // Logic to handle location object
                }
            }
        });
```
