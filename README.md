# Flutter Forsted/Glass App Bar


## Getting Started

Simply add following snippet as your Sliver App Bar and use it inside your custom scroll view.

```
class FrostedAppBar extends StatelessWidget {
  final String title;
  final List<Widget> actions;
  final bool
      showLeading; //Controls whether we should try to imply the leading widget

  const FrostedAppBar(
      {Key key, @required this.title, this.actions, this.showLeading = false})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return SliverAppBar(
      expandedHeight: 100,
      automaticallyImplyLeading: showLeading,
      backgroundColor: Colors.transparent,
      flexibleSpace: ClipRect(
        child: BackdropFilter(
          filter: ImageFilter.blur(
            sigmaX: 10,
            sigmaY: 10,
          ),
          child: FlexibleSpaceBar(
            titlePadding: const EdgeInsets.all(8.0),
            title: Text(
              title,
              style: Theme.of(context)
                  .textTheme
                  .headline6
                  .copyWith(fontWeight: FontWeight.bold),
            ),
          ),
        ),
      ),
      pinned: true,
      //Whether the app bar should remain visible at the start of the scroll view
      floating: false,
      //Whether the app bar should become visible as soon as the user scrolls towards the app bar.
      snap: false,
      actions: actions ?? [],
    );
  }
}
```

