import React, { useState } from 'react';
import { View, Text, StyleSheet } from 'react-native';
import GestureRecognizer, { swipeDirections } from 'react-native-swipe-gestures';

const CardCounter = () => {
  const [count, setCount] = useState(0);
  const [trueCount, setTrueCount] = useState(0);

  const handleSwipe = (gestureName) => {
    switch (gestureName) {
      case swipeDirections.SWIPE_UP:
        setCount(count + 1);
        break;
      case swipeDirections.SWIPE_DOWN:
        setCount(count - 1);
        break;
      case swipeDirections.SWIPE_LEFT:
        // Burn card
        break;
      case swipeDirections.SWIPE_RIGHT:
        setCount(0); // Reset count
        break;
    }
  };

  return (
    <GestureRecognizer
      onSwipe={(direction) => handleSwipe(direction)}
      config={{ velocityThreshold: 0.3, directionalOffsetThreshold: 80 }}
    >
      <View style={styles.container}>
        <Text style={styles.text}>Running Count: {count}</Text>
        <Text style={styles.text}>True Count: {trueCount}</Text>
      </View>
    </GestureRecognizer>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
    backgroundColor: '#fff',
  },
  text: {
    fontSize: 20,
    marginBottom: 10,
  },
});

export default CardCounter;
