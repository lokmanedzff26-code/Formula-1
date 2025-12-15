const races = {
  algeria: { time: '14:00', date: '2025-12-22' },
  saudi: { time: '16:00', date: '2025-12-22' }
};

function updateTimes() {
  const country = document.getElementById('country').value;
  const race = races[country];
  document.getElementById('time').innerText = race.time;
  document.getElementById('date').innerText = `📅 التاريخ: ${race.date}`;
}

// عد تنازلي
function startCountdown() {
  const raceDate = new Date('2025-12-22T14:00:00'); // بتوقيت الجزائر
  const countdownEl = document.getElementById('countdown');

  function updateCountdown() {
    const now = new Date();
    const diff = raceDate - now;
    if (diff <= 0) {
      countdownEl.innerText = "🏁 السباق بدأ!";
      clearInterval(interval);
      return;
    }
    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
    const minutes = Math.floor((diff / (1000 * 60)) % 60);
    const seconds = Math.floor((diff / 1000) % 60);
    countdownEl.innerText = `${days} يوم ${hours} ساعة ${minutes} دقيقة ${seconds} ثانية`;
  }

  updateCountdown();
  const interval = setInterval(updateCountdown, 1000);
}

updateTimes();
startCountdown();
