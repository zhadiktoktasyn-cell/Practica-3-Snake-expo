import React, { useState } from 'react';

import {
  View,
  Text,
  Image,
  FlatList,
  StyleSheet,
  StatusBar,
  Switch,
  SafeAreaView,
} from 'react-native';

const languages = [
  {
    day: 1,
    title: 'JavaScript',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg',
    description:
      'JavaScript — популярный язык программирования, который широко используется для создания интерактивных веб-сайтов и приложений.',
    additional:
      'Типизация: динамическая. Основная область: веб-разработка.',
  },
  {
    day: 2,
    title: 'Python',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg',
    description:
      'Python — универсальный язык программирования с простым и понятным синтаксисом. Он используется в разработке программ, анализе данных и искусственном интеллекте.',
    additional:
      'Типизация: динамическая. Основная область: универсальная разработка.',
  },
  {
    day: 3,
    title: 'Java',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/java/java-original.svg',
    description:
      'Java — объектно-ориентированный язык программирования, используемый для серверных приложений, корпоративных систем и Android-разработки.',
    additional:
      'Типизация: статическая. Основная область: корпоративная разработка.',
  },
  {
    day: 4,
    title: 'C++',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/cplusplus/cplusplus-original.svg',
    description:
      'C++ — производительный язык программирования, который применяется для системного программирования, игр и приложений, требующих высокой скорости.',
    additional:
      'Типизация: статическая. Основная область: системное и игровое программирование.',
  },
  {
    day: 5,
    title: 'C#',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/csharp/csharp-original.svg',
    description:
      'C# — современный язык программирования от Microsoft. Используется для создания приложений, серверных систем и компьютерных игр.',
    additional:
      'Типизация: статическая. Основная область: .NET и разработка игр.',
  },
  {
    day: 6,
    title: 'Kotlin',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/kotlin/kotlin-original.svg',
    description:
      'Kotlin — современный язык программирования, который широко применяется для разработки Android-приложений.',
    additional:
      'Типизация: статическая. Основная область: Android-разработка.',
  },
  {
    day: 7,
    title: 'Swift',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/swift/swift-original.svg',
    description:
      'Swift — язык программирования компании Apple. Он используется для создания приложений для iPhone, iPad и Mac.',
    additional:
      'Типизация: статическая. Основная область: iOS и macOS.',
  },
  {
    day: 8,
    title: 'Go',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/go/go-original.svg',
    description:
      'Go — компилируемый язык программирования, созданный в Google. Он ориентирован на простоту, производительность и параллельное выполнение задач.',
    additional:
      'Типизация: статическая. Основная область: серверные приложения.',
  },
  {
    day: 9,
    title: 'Rust',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/rust/rust-original.svg',
    description:
      'Rust — системный язык программирования, ориентированный на высокую производительность и безопасность работы с памятью.',
    additional:
      'Типизация: статическая. Основная область: системное программирование.',
  },
  {
    day: 10,
    title: 'PHP',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/php/php-original.svg',
    description:
      'PHP — язык программирования, который широко используется для создания серверной части веб-сайтов и веб-приложений.',
    additional:
      'Типизация: динамическая. Основная область: веб-разработка.',
  },
  {
    day: 11,
    title: 'Ruby',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/ruby/ruby-original.svg',
    description:
      'Ruby — язык программирования с удобным и выразительным синтаксисом. Он известен благодаря фреймворку Ruby on Rails.',
    additional:
      'Типизация: динамическая. Основная область: веб-разработка.',
  },
  {
    day: 12,
    title: 'Dart',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/dart/dart-original.svg',
    description:
      'Dart — язык программирования компании Google. Он используется в качестве основного языка фреймворка Flutter.',
    additional:
      'Типизация: статическая. Основная область: мобильная разработка.',
  },
  {
    day: 13,
    title: 'TypeScript',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/typescript/typescript-original.svg',
    description:
      'TypeScript расширяет JavaScript системой типов и помогает создавать более крупные и структурированные приложения.',
    additional:
      'Типизация: статическая. Основная область: веб-разработка.',
  },
  {
    day: 14,
    title: 'R',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/r/r-original.svg',
    description:
      'R — язык программирования для статистических вычислений, анализа данных и создания научных графиков.',
    additional:
      'Типизация: динамическая. Основная область: статистика и анализ данных.',
  },
  {
    day: 15,
    title: 'Scala',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/scala/scala-original.svg',
    description:
      'Scala сочетает объектно-ориентированный и функциональный подходы и работает на виртуальной машине Java.',
    additional:
      'Типизация: статическая. Основная область: серверные системы.',
  },
  {
    day: 16,
    title: 'Perl',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/perl/perl-original.svg',
    description:
      'Perl — язык программирования, известный своими возможностями обработки текста, строк и автоматизации задач.',
    additional:
      'Типизация: динамическая. Основная область: автоматизация и обработка текста.',
  },
  {
    day: 17,
    title: 'Lua',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/lua/lua-original.svg',
    description:
      'Lua — лёгкий и быстрый язык программирования, который часто используется внутри игр и других программ.',
    additional:
      'Типизация: динамическая. Основная область: игры и сценарии.',
  },
  {
    day: 18,
    title: 'Haskell',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/haskell/haskell-original.svg',
    description:
      'Haskell — функциональный язык программирования с сильной статической типизацией.',
    additional:
      'Типизация: статическая. Основная область: функциональное программирование.',
  },
  {
    day: 19,
    title: 'Elixir',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/elixir/elixir-original.svg',
    description:
      'Elixir — функциональный язык программирования, работающий на виртуальной машине Erlang и подходящий для распределённых систем.',
    additional:
      'Типизация: динамическая. Основная область: распределённые системы.',
  },
  {
    day: 20,
    title: 'Erlang',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/erlang/erlang-original.svg',
    description:
      'Erlang создавался для систем, которым необходима высокая доступность и возможность обработки большого количества параллельных процессов.',
    additional:
      'Типизация: динамическая. Основная область: телекоммуникации.',
  },
  {
    day: 21,
    title: 'Objective-C',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/objectivec/objectivec-plain.svg',
    description:
      'Objective-C — язык программирования, который исторически широко применялся для разработки программ Apple.',
    additional:
      'Типизация: статическая. Основная область: Apple-разработка.',
  },
  {
    day: 22,
    title: 'D',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/d/d-original.svg',
    description:
      'D — системный язык программирования, сочетающий высокую производительность и возможности современных языков.',
    additional:
      'Типизация: статическая. Основная область: системная разработка.',
  },
  {
    day: 23,
    title: 'Julia',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/julia/julia-original.svg',
    description:
      'Julia создана для научных вычислений и численных задач. Она сочетает удобный синтаксис и высокую производительность.',
    additional:
      'Типизация: динамическая. Основная область: научные вычисления.',
  },
  {
    day: 24,
    title: 'Groovy',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/groovy/groovy-original.svg',
    description:
      'Groovy — динамический язык программирования, работающий на платформе Java. Он используется для автоматизации и разработки приложений.',
    additional:
      'Типизация: динамическая. Основная область: Java-экосистема.',
  },
  {
    day: 25,
    title: 'Fortran',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/fortran/fortran-original.svg',
    description:
      'Fortran — один из первых высокоуровневых языков программирования. Он продолжает использоваться для научных и инженерных вычислений.',
    additional:
      'Основная область: научные и инженерные расчёты.',
  },
  {
    day: 26,
    title: 'C',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/c/c-original.svg',
    description:
      'C — один из наиболее известных системных языков программирования. Он предоставляет низкоуровневый доступ к памяти и аппаратным ресурсам.',
    additional:
      'Типизация: статическая. Основная область: системное программирование.',
  },
  {
    day: 27,
    title: 'F#',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/fsharp/fsharp-original.svg',
    description:
      'F# — функциональный язык программирования из экосистемы .NET. Он поддерживает функциональный и объектно-ориентированный подходы.',
    additional:
      'Типизация: статическая. Основная область: .NET.',
  },
  {
    day: 28,
    title: 'Solidity',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/solidity/solidity-original.svg',
    description:
      'Solidity — язык программирования, предназначенный для создания смарт-контрактов в блокчейн-сетях.',
    additional:
      'Основная область: блокчейн и смарт-контракты.',
  },
  {
    day: 29,
    title: 'Zig',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/zig/zig-original.svg',
    description:
      'Zig — системный язык программирования, ориентированный на контроль ресурсов, производительность и простоту.',
    additional:
      'Типизация: статическая. Основная область: системное программирование.',
  },
  {
    day: 30,
    title: 'HTML',
    image:
      'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg',
    description:
      'HTML используется для создания структуры веб-страниц. С его помощью определяются заголовки, изображения, текст, ссылки и другие элементы страницы.',
    additional:
      'Основная область: веб-разработка.',
  },
];

export default function App() {
  const [darkMode, setDarkMode] = useState(false);

  const theme = darkMode ? darkTheme : lightTheme;

  const renderLanguage = ({ item }) => {
    return (
      <View
        style={[
          styles.card,
          {
            backgroundColor: theme.card,
            shadowColor: darkMode ? '#000000' : '#607D8B',
          },
        ]}
      >
        <View style={styles.dayContainer}>
          <Text
            style={[
              styles.dayText,
              {
                color: theme.secondary,
              },
            ]}
          >
            День {item.day}
          </Text>
        </View>

        <Text
          style={[
            styles.title,
            {
              color: theme.text,
            },
          ]}
        >
          {item.title}
        </Text>

        <Image
          source={{ uri: item.image }}
          style={styles.image}
          resizeMode="contain"
        />

        <Text
          style={[
            styles.description,
            {
              color: theme.textSecondary,
            },
          ]}
        >
          {item.description}
        </Text>

        <View
          style={[
            styles.additionalContainer,
            {
              backgroundColor: theme.additionalBackground,
            },
          ]}
        >
          <Text
            style={[
              styles.additional,
              {
                color: theme.textSecondary,
              },
            ]}
          >
            {item.additional}
          </Text>
        </View>
      </View>
    );
  };

  return (
    <SafeAreaView
      style={[
        styles.container,
        {
          backgroundColor: theme.background,
        },
      ]}
    >
      <StatusBar
        barStyle={darkMode ? 'light-content' : 'dark-content'}
        backgroundColor={theme.background}
      />

      <View
        style={[
          styles.header,
          {
            backgroundColor: theme.background,
          },
        ]}
      >
        <View style={styles.headerText}>
          <Text
            style={[
              styles.appTitle,
              {
                color: theme.text,
              },
            ]}
          >
            30 Days of Programming
          </Text>

          <Text
            style={[
              styles.appSubtitle,
              {
                color: theme.textSecondary,
              },
            ]}
          >
            Языки программирования
          </Text>
        </View>

        <View style={styles.themeSwitch}>
          <Text style={styles.themeIcon}>
            {darkMode ? '🌙' : '☀️'}
          </Text>

          <Switch
            value={darkMode}
            onValueChange={setDarkMode}
            trackColor={{
              false: '#C5D6CC',
              true: '#6B4FA3',
            }}
            thumbColor={darkMode ? '#FFFFFF' : '#2E7D5B'}
          />
        </View>
      </View>

      <FlatList
        data={languages}
        keyExtractor={(item) => item.day.toString()}
        renderItem={renderLanguage}
        showsVerticalScrollIndicator={false}
        contentContainerStyle={styles.list}
        ItemSeparatorComponent={() => (
          <View style={styles.separator} />
        )}
      />
    </SafeAreaView>
  );
}

const lightTheme = {
  background: '#F4F7F5',
  card: '#FFFFFF',
  text: '#263238',
  textSecondary: '#59666B',
  secondary: '#2E7D5B',
  additionalBackground: '#E8F1EC',
};

const darkTheme = {
  background: '#121816',
  card: '#1E2925',
  text: '#F1F5F3',
  textSecondary: '#C2CCC7',
  secondary: '#8BC9A7',
  additionalBackground: '#293832',
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },

  header: {
    paddingHorizontal: 20,
    paddingTop: 15,
    paddingBottom: 15,
    flexDirection: 'row',
    alignItems: 'center',
    justifyContent: 'space-between',
  },

  headerText: {
    flex: 1,
    paddingRight: 10,
  },

  appTitle: {
    fontSize: 24,
    fontWeight: '700',
  },

  appSubtitle: {
    fontSize: 14,
    marginTop: 5,
  },

  themeSwitch: {
    alignItems: 'center',
    flexDirection: 'row',
    gap: 5,
  },

  themeIcon: {
    fontSize: 20,
  },

  list: {
    paddingHorizontal: 16,
    paddingTop: 8,
    paddingBottom: 30,
  },

  card: {
    borderRadius: 18,
    padding: 14,
    elevation: 4,

    shadowOffset: {
      width: 0,
      height: 3,
    },

    shadowOpacity: 0.15,
    shadowRadius: 6,
  },

  dayContainer: {
    marginBottom: 5,
  },

  dayText: {
    fontSize: 14,
    fontWeight: '600',
  },

  title: {
    fontSize: 22,
    fontWeight: '600',
    marginBottom: 12,
  },

  image: {
    width: '100%',
    height: 180,
    borderRadius: 12,
    backgroundColor: '#F2F2F2',
    marginBottom: 12,
  },

  description: {
    fontSize: 15,
    lineHeight: 22,
  },

  additionalContainer: {
    borderRadius: 10,
    padding: 10,
    marginTop: 12,
  },

  additional: {
    fontSize: 13,
    lineHeight: 19,
  },

  separator: {
    height: 14,
  },
});
