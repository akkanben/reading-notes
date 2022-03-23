# Reading Notes 28 -- RecyclerView

From [Googles Android Docs](https://developer.android.com/guide/topics/ui/layout/recyclerview#java)

## RecyclerView

The RecyclerView can create dynamic lists when provided with a data set. Item appearance is defined and RecyclerView creates the items and displays them in a power efficient way. The recyclerview resuses elements as they scroll off the screen instead of destroying them.

- `RecyclerView` is a ViewGroup that needs to be added to the layout.
- `RecyclerView.ViewHolder` is used to define the view. This is a wrapper around the view.
- `RecyclerView.Adapter` holds methods that bind the views to their data.
- A layout manager can be custom defined or borrowed from the RecyclerView library.

### Using RecyclerView

Planning is required to use the RecyclerView well. 

- Decide on a layout for what the list or grid of data will look like.
- Use a built-in or custom layout.
  - `LinearLayoutManager` one-dimentional list.
  - `GridLayoutManager` two-dimentional grid. Can be horizontal or vertical.
  - `StaggeredGridLayoutManager` allows for layouts that have offset rows or columns.
- Design the look of how the items will appear in the layout. By extending the ViewHolder you can implement your own item appearance.
- Define the Adapter for the data by overriding 3 methods:
  - `onCreateViewHolder()` creates an empty ViewHolder.
  - `onBindViewHolder()` fills the view with data.
  - `getItemCount()` returns the size of the data set.

## Example from the Docs

```java
public class CustomAdapter extends RecyclerView.Adapter<CustomAdapter.ViewHolder> {

    private String[] localDataSet;

    /**
     * Provide a reference to the type of views that you are using
     * (custom ViewHolder).
     */
    public static class ViewHolder extends RecyclerView.ViewHolder {
        private final TextView textView;

        public ViewHolder(View view) {
            super(view);
            // Define click listener for the ViewHolder's View

            textView = (TextView) view.findViewById(R.id.textView);
        }

        public TextView getTextView() {
            return textView;
        }
    }

    /**
     * Initialize the dataset of the Adapter.
     *
     * @param dataSet String[] containing the data to populate views to be used
     * by RecyclerView.
     */
    public CustomAdapter(String[] dataSet) {
        localDataSet = dataSet;
    }

    // Create new views (invoked by the layout manager)
    @Override
    public ViewHolder onCreateViewHolder(ViewGroup viewGroup, int viewType) {
        // Create a new view, which defines the UI of the list item
        View view = LayoutInflater.from(viewGroup.getContext())
                .inflate(R.layout.text_row_item, viewGroup, false);

        return new ViewHolder(view);
    }

    // Replace the contents of a view (invoked by the layout manager)
    @Override
    public void onBindViewHolder(ViewHolder viewHolder, final int position) {

        // Get element from your dataset at this position and replace the
        // contents of the view with that element
        viewHolder.getTextView().setText(localDataSet[position]);
    }

    // Return the size of your dataset (invoked by the layout manager)
    @Override
    public int getItemCount() {
        return localDataSet.length;
    }
}

```

