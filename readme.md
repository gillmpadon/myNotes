# Link for Creaating Expo app with native wind
// https://medium.com/@simpleandshort/how-to-use-nativewind-tailwindcss-in-your-react-native-application-67874f41e13f

Step 1:
    yarn create expo-app <appname>
    cd <appname>
    yarn expo start

    //adding of tailwind
    
    yarn add nativewind 
    yarn add --dev tailwindcss

    npx tailwindcss init

    // tailwind.config.js

    module.exports = {
    content: ["./App.{js,jsx,ts,tsx}", "./<custom directory>/**/*.{js,jsx,ts,tsx}"],
    theme: {
        extend: {},
    },
    plugins: [],
    }

    // babel.config.js
    module.exports = function (api) {
    api.cache(true);
    return {
        presets: ["babel-preset-expo"],
        plugins: ["nativewind/babel"],
    };
    };

    yarn add --dev tailwindcss@3.3.2

    
# Adding React native svg

Step 1: 
    yarn add react-native-svg
    yarn add --dev react-native-svg-transformer

    create metro.config.js

    // metro.config.js
    const { getDefaultConfig } = require("expo/metro-config");

    module.exports = (() => {
    const config = getDefaultConfig(__dirname);

    const { transformer, resolver } = config;

    config.transformer = {
        ...transformer,
        babelTransformerPath: require.resolve("react-native-svg-transformer")
    };
    config.resolver = {
        ...resolver,
        assetExts: resolver.assetExts.filter((ext) => ext !== "svg"),
        sourceExts: [...resolver.sourceExts, "svg"]
    };

    return config;
    })();


Step 2:
    Utilize SVG to React Plugins in Figma
    Only get the SVG tag and its imports, use export default function(props){}

    //This will Allow you to Save the SVG
    yarn add react-native-svg --save

    //Try Restarting Server and Open it Again
    <!-- 
    Some dependencies are incompatible with the installed expo version:
    react-native-svg@13.13.0 - expected version: 13.9.0
    Your project may not work correctly until you install the correct versions of the packages.
    Fix with: npx expo install --fix

    You will see this but bruh, it should work
 -->


Step 3:
    Utilize free vector icons in react native
    import Icon from '@expo/vector-icons/FontAwesome'
    <View className="mt-2">
        <Icon  name='facebook' size={32} color="red" />
    </View>






# Possible Errors
    1. If encounter is cancelled depreciated use canceled instead 
     if (!result.canceled) {
      setImage(result.assets[0].uri)
      setShowSticker(true)
    }else{
      alert("You need to select an image")
    }